---
title: "在 Visual Studio 中使用 C++ 和 Python | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "在 Visual Studio 中撰寫適用於 Python 的 C++ 延伸模組或模組的程序和步驟"
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 21a413a3e2d17d77fd83d5109587a96f323a0511
ms.openlocfilehash: 1912afdba22d9dec6ee3f68aafc78c07779a5b3c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---

# <a name="creating-a-c-extension-for-python"></a>建立適用於 Python 的 C++ 延伸模組

以 C++ (或 C) 撰寫的模組通常用於延伸 Python 解譯器的功能，以及啟用低階作業系統功能的存取。 有三個主要類型的模組︰

- 加速器模組︰因為 Python 是解譯的語言，可以用 C++ 撰寫特定程式碼以獲得更高的效能。 
- 包裝函式模組：包裝函式會向 Python 程式碼公開現有的 C/C++ 介面，或公開來自 Python、容易使用且更「Python 化」的 API。
- 低層級的系統存取模組︰建立以存取 CPython 執行階段、作業系統或基礎硬體的較低層級功能。 

本主題會逐步建置適用於 CPython 的 C++ 延伸模組，計算雙曲線正切函數，並從 Python 程式碼呼叫它。 常式先以 Python 實作，以示範用 C++ 實作相同常式時的效能改善。

這裡採用的方法是針對標準 CPython 延伸模組，如 [Python 文件](https://docs.python.org/3/c-api/)中所述。 此方法與其他方法之間的比較，描述於本主題結尾的[替代方法](#alternative-approaches)。

## <a name="prerequisites"></a>必要條件

本逐步解說是針對 Visual Studio 2017 所撰寫，並且具有**使用 C++ 的桌面開發**和 **Python 開發**工作負載，及其預設選項 (例如使用 Python 3.6 作為預設解譯器)。 在 [Python 開發] 工作負載中，也請核取 Python 原生開發工具右邊的方塊，它會設定本主題中所述的大部分選項。 (這個選項也會自動包含 C++ 工作負載。) 

![選取 Python 原生開發工具選項](media/cpp-install-native.png)

如需詳細資訊，請參閱[為 Visual Studio 安裝 Python 支援](installation.md)，包括使用 Visual Studio 的其他版本。 如果您分別安裝 Python，請務必在安裝程式的 [進階選項] 下，選取 [下載偵錯符號] 和 [下載偵錯二進位檔案]。 這個選項可確保如果您選擇進行偵錯組建，您可以使用必要的偵錯程式庫。

> [!Note]
> Python 也可透過包含 64 位元的 Anaconda 3 (含最新版 CPython) 和預設 [Python 原生開發工具] 選項的**資料科學和分析應用程式**工作負載取得。

## <a name="create-the-python-application"></a>建立 Python 應用程式

1. 在 Visual Studio 中建立新的 Python 專案，方法是選取 [檔案] > [新增] > [專案]。 搜尋 Python、選取 [Python 應用程式] 範本、提供適合的名稱和位置，並選取 [確定]。

1. 在專案的 `.py` 檔案中，貼上下列程式碼，以為雙曲線正切函數的計算進行基準測試 (實作時不使用數學程式庫，以方便比較)。 您可以隨意以手動方式輸入程式碼，來體驗一些 [Python 編輯功能](code-editing.md)。

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tanger function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()

        result = fn(DATA)

        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. 使用 [偵錯] > [啟動但不偵錯] (Ctrl + F5) 執行程式，來查看結果。 每個基準測試需要數秒才能完成。

## <a name="create-the-core-c-project"></a>建立核心 C++ 專案

1. 在方案總管中，以滑鼠右鍵按一下解決方案，然後選取 [新增] > [新增專案]。Visual Studio 解決方案可以同時包含 Python 和 C++ 專案。

1. 搜尋 "C++"、選取 [空專案]、指定名稱 (例如 TanhBenchmark)，然後選取 [確定]。 注意︰如果您已經與 Visual Studio 2017 一起安裝 **Python 原生開發工具**，您可以從 [Python 延伸模組] 範本開始，它已經使用了此處描述的許多功能。 不過，在此逐步解說中，從空白專案開始將逐步示範如何建置延伸模組。

1. 在新專案中建立 C++ 檔案，方法是以滑鼠右鍵按一下 [原始程式檔] 節點，然後選取 [新增] > [新增項目...]、選取 [C++ 檔案]、提供名稱 (例如 `module.cpp`)，然後選取 [確定]。 需要執行此步驟，才能在接下來的步驟開啟 C++ 屬性頁。

1. 以滑鼠右鍵按一下新專案，然後選取 屬性，在出現的 屬性頁 對話方塊上方，將 組態 設定為 所有組態。

1. 如下所述設定特定的屬性，然後選取 [套用] (您可能需要在可編輯的欄位外按一下，[套用] 按鈕才會變成啟用狀態)。

    | 索引標籤 | 屬性 | 值 | 
    | --- | --- | --- |
    | 一般 | 一般 > 目標名稱 | 將此欄位設為完全符合 Python 所見的模組名稱。 |
    | | 一般 > 目標副檔名 | .pyd |
    | | 專案預設值 > 組態類型 | 動態程式庫 (.dll) |
    | C/C++ > 一般 | 其他 Include 目錄 | 視您的安裝新增適當的 Python `include` 資料夾，例如 `c:\Python36\include` |     
    | C/C++ > 程式碼產生 | 執行階段程式庫 | 多執行緒的 DLL (/ MD) (請參閱下列警告) |
    | C/C++ > 前置處理器 | 前置處理器定義 | 將 `Py_LIMITED_API;` 新增到字串的開頭會限制您可以從 Python 呼叫的某些功能，並使程式碼更容易在不同版本的 Python 之間移植。 |
    | 連結器 > 一般 | 其他程式庫目錄 | 視您的安裝新增適當的 Python `lib` 資料夾並包含 `.lib` 檔案，例如 `c:\Python36\libs` (請務必指向包含 `.lib` 檔案的 `libs` 資料夾，而「不是」包含 `.py` 檔案的 `Lib` 資料夾。) | 

    > [!Tip]
    > 如果您沒有看到 [C/C++] 索引標籤，這是因為專案不包含它識別為 C/C++ 原始程式檔的任何檔案。 如果您建立原始程式檔，而沒有 `.c` 或 `.cpp` 副檔名，便可能發生此情形。 比方說，如果您稍早在新項目對話方塊中不小心輸入 `module.coo` 而不是 `module.cpp`，則 Visual Studio 會建立此檔案，但不會將檔案類型設定為「C/C++ 程式碼」，「C/C++ 程式碼」會啟動 [C/C++ 屬性] 索引標籤。即使用 `.cpp` 重新命名您的檔案，仍會發生這種錯誤識別。 若要正確設定檔案類型，請在方案總管中以滑鼠右鍵按一下檔案、選取 [屬性]，然後將 [檔案類型] 設定為 [C/C++ 程式碼]。

    > [!Warning]
    > 請不要將 [C/C++] > [產生程式碼] > [執行階段程式庫] 選項設定為 [多執行緒偵錯 DLL (/MDd)]，即使是針對偵錯組態。 請選取 [多執行緒 DLL (/MD)] 執行階段，因為非偵錯 Python 二進位碼檔案是使用它所建置。 如果您剛好設定 /MDd 選項，您會在建置 DLL 的偵錯組態時看到錯誤「C1189: Py_LIMITED_API 與 Py_DEBUG、Py_TRACE_REFS 和 Py_REF_DEBUG 不相容」。 此外，如果您移除 `Py_LIMITED_API` 以避免發生建置錯誤，Python 會在嘗試匯入模組時當機。 (當機會發生在 DLL 的 `PyModule_Create` 呼叫內，如稍後所述，輸出訊息為「Python 嚴重錯誤︰PyThreadState_Get︰沒有目前的執行緒」。)
    >
    > 請注意，/MDd 選項用來建置 Python 偵錯二進位檔案 (例如 python_d.exe)，但針對延伸模組 DLL 選取它仍會導致 `Py_LIMITED_API` 建置錯誤。
   
1. 以滑鼠右鍵按一下 C++ 專案，然後選取 [建置] 來測試您的組態 (偵錯和發行)。 `.pyd` 檔案位於 **Debug** 和 **Release** 下的 *solution* 資料夾，而不是 C++ 專案資料夾本身。

1. 將下列程式碼加入 C++ 專案的主要 `.cpp` 檔案︰

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh(double x) {
        return sinh(x) / cosh(x);
    }
    ```

1. 重新建置 C++ 專案，確認您的程式碼正確。


## <a name="convert-the-c-project-to-an-extension-for-python"></a>將 C++ 專案轉換成適用於 Python 的延伸模組

若要使 C++ DLL 變成適用於 Python 的延伸模組，您需要修改匯出的方法以和 Python 類型互動。 然後，您需要新增匯出模組的函式，以及模組方法的定義。 如需這裡所顯示內容的背景，請參閱 [Python/C API 參考手冊](https://docs.python.org/3/c-api/index.html)，以及尤其是 python.org 上的[模組物件](https://docs.python.org/3/c-api/module.html)。(切記從右上方的下拉式清單控制項中選取您的 Python 版本。)

1. 在 C++ 檔案中，在頂端包含 `Python.h`：

    ```cpp
    #include <Python.h>
    ```

1. 修改 `tanh` 方法以接受並傳回 Python 類型︰

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. 新增結構，定義 C++ `tanh` 函式如何向 Python 呈現：

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. 新增結構，定義 Python 將看到的模組︰

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. 新增方法，當 Python 載入模組時會呼叫該方法，它必須命名為 `PyInit_<module-name>`，其中 &lt;模組名稱&gt; 完全符合 C++ 專案的 [一般] > [目標名稱] 屬性 (亦即，它符合專案所建置之 `.pyd` 的檔名)。

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. 重新建置 DLL，確認您的程式碼。

## <a name="test-the-code-and-compare-the-results"></a>測試程式碼，並比較結果

現在您已將 DLL 結構化成為 Python 延伸模組，您可以從 Python 專案參考它、匯入模組，並使用其方法。

有兩種方式，可讓 Python 使用 DLL。 首先，您可以新增從 Python 專案對 C++ 專案的參考，前提是它們在相同的 Visual Studio 解決方案中︰

1. 在方案總管中，以滑鼠右鍵按一下 [Python 專案]，然後選取 [參考]。 在對話方塊中，依序選取 [專案] 索引標籤、[superfastcode] 專案、[確定]。

第二，您可以將模組安裝在全域 Python 環境中，將它也提供給其他 Python 專案使用。 這樣做，通常需要您重新整理該環境的 IntelliSense 完成資料庫。 從環境移除模組時，也需要重新整理。

1. 如果您使用 Visual Studio 2017，請執行 Visual Studio 安裝程式，然後依序選取 [修改]、[個別元件] > [編譯器、建置工具和執行階段] > [Visual C++ 2015.3 v140 工具組]。 此步驟之所以必要，是因為 Python (適用於 Windows) 本身是使用 Visual Studio 2015 (14.0 版) 所建置，並預期在透過此處所述方法建置延伸模組時，這些工具可供使用。

1. 在 C++ 專案中建立名為 `setup.py` 的檔案，方法是以滑鼠右鍵按一下專案，選取 [新增] > [新增項目...]，搜尋 "Python" 並選取 [Python 檔案]，將它命名為 setup.py，然後選取 [確定]。 當檔案出現在編輯器中時，將下列程式碼貼入其中︰

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    如需有關此指令碼的文件，請參閱 [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (建置 C 和 C++ 延伸模組) (python.org)。

1. `setup.py` 程式碼會指示 Python 建置延伸模組 (使用 Visual Studio 2015 C++ 工具組)，這是從命令列發生。 開啟提升權限的命令提示字元、巡覽至包含 C++ 專案 (和 `setup.py`) 的資料夾，然後輸入下列命令︰

    ```bash
    pip install .
    ```

現在您可以呼叫 `tanh` 程式碼模組，並比較它和 Python 實作的效能︰

1. 在 `tanhbenchmark.py` 新增以下幾行，呼叫從 DLL 匯出的 `fast_tanh` 方法，並將它加入基準測試輸出。 如果您以手動方式輸入 `from s` 陳述式，則會看到 `superfastcode` 出現在完成清單中，且輸入 `import` 之後會出現 `fast_tanh` 方法。

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. 執行 Python 程式，您會看到 C++ 常式執行速度比 Python 實作快約 15 到 20 倍。

## <a name="debug-the-c-code"></a>偵錯 C++ 程式碼

[Visual Studio 中的 Python 支援](installation.md)包括能夠[同時偵錯 Python 和 C++ 程式碼](debugging-mixed-mode.md)。 若要體驗此混合模式偵錯，請執行下列步驟：

1. 在方案總管中以滑鼠右鍵按一下 Python 專案、依序選取 [屬性]、[偵錯] 索引標籤，然後選取 [偵錯] > [啟用機器碼偵錯] 的選項。

    > [!Tip]
    > 當您啟用機器碼偵錯時，Python 的輸出視窗可能會在程式完成時立即消失，而不給您平常的「按任意鍵繼續...」暫停。 若要強制暫停，當您啟用機器碼偵錯時，請將 `-i` 選項加入 [偵錯] 索引標籤上的 [執行] > [解譯器引數] 欄位。 這個引數會讓 Python 解譯器在程式碼完成之後進入互動模式，等候您按下 Ctrl + Z、Enter 以結束。 (或者，如果您不介意修改 Python 程式碼，可以在程式結尾新增 `import os` 和 `os.system("pause")` 陳述式。 此程式碼會複製原始暫停提示字元。)

1. 在您的 C++ 程式碼中，在 `tanh` 方法內的第一行設定中斷點，然後啟動偵錯工具。 偵錯工具在呼叫該程式碼時停止︰

    ![在 C++ 程式碼的中斷點處停止](media/cpp-debugging.png)

1. 此時您可以逐步執行 C++ 程式碼、檢查變數等等，如[同時偵錯 Python 和 C++ 程式碼](debugging-mixed-mode.md)中所述。

## <a name="alternative-approaches"></a>替代方法 

有其他方式可建立 Python 延伸模組，如下表所述。 CPython 的第一個項目已經在這個主題中討論。

| 方法 | 年分 | 代表使用者 | 正面意見 | 反面意見 |
| --- | --- | --- | --- | --- |
| 適用於 CPython 的 C/C++ 延伸模組 | 1991 | 標準程式庫 | [大量文件與教學課程](https://docs.python.org/3/c-api/)。 完全控制。 | 編譯、可攜性、參考管理。 高度 C 知識。 |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 一次產生許多語言的繫結。 | 如果 Python 是唯一的目標，負荷會過大。 |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 不需編譯、廣泛可用。 | 存取與變更 C 結構麻煩又容易出錯。 |
| Cython | 2007 | [gevent](http://www.gevent.org/)、[kivy](https://kivy.org/) | 類似 Python。 高度成熟。 高效能。 | 編譯、新的語法和工具鏈。 |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/)、[pypy](http://pypy.org/) | 輕鬆整合、PyPy 相容性。 | 新穎、較不成熟。 |

