---
title: 撰寫適用於 Python 的 C++ 延伸模組
description: 使用 Visual Studio、CPython 和 PyBind11 建立適用於 Python 的 C++ 延伸模組逐步解說，包括混合模式偵錯。
ms.date: 11/19/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 461e68979de6c3b711c05cc4be3ef9d5bd761397
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885933"
---
# <a name="create-a-c-extension-for-python"></a>建立適用於 Python 的 C++ 延伸模組

以 C++ (或 C) 撰寫的模組通常用於延伸 Python 解譯器的功能，以及啟用低階作業系統功能的存取。 有三個主要類型的模組︰

- 加速器模組︰因為 Python 是解譯的語言，可以用 C++ 撰寫特定程式碼以獲得更高的效能。
- 包裝函式模組：向 Python 程式碼公開現有的 C/C++ 介面，或公開來自 Python、容易使用且更具「Python 風格」的 API。
- 低層級的系統存取模組︰建立以存取 CPython 執行階段、作業系統或基礎硬體的較低層級功能。

本文會逐步建置適用於 CPython 的 C++ 延伸模組，計算雙曲線正切函數，並從 Python 程式碼呼叫它。 常式先以 Python 實作，以示範用 C++ 實作相同常式時的相對效能改善。

本文也會示範兩種方式，讓 Python 可使用 C++：

- 標準 CPython 延伸模組，如 [Python 文件](https://docs.python.org/3/c-api/)中所述
- [PyBind11](https://github.com/pybind/pybind11)，針對 C++ 11 建議使用，因為其單純性。

這些方法與其他方法之間的比較，描述於本文結尾的[替代方法](#alternative-approaches)中。

您可於 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) 找到此逐步解說的完整範例。

## <a name="prerequisites"></a>必要條件

- Visual Studio 2017 或更新版本含有使用預設選項安裝的 **使用 C++ 的桌面開發** 和 **Python 開發** 工作負載。
- 在 **Python 開發** 工作負載中，也選取 **Python 原生開發工具** 右邊的方塊。 這個選項會設定本文所述的大部分組態。 (這個選項也會自動包含 C++ 工作負載。)

    ![選取 Python 原生開發工具選項](media/cpp-install-native.png)

    > [!Tip]
    > 安裝 [資料科學和分析應用程式] 工作負載時，預設也會包含 Python 和 [Python 原生開發工具] 選項。

如需詳細資訊，請參閱[為 Visual Studio 安裝 Python 支援](installing-python-support-in-visual-studio.md)，包括使用 Visual Studio 的其他版本。 如果您分別安裝 Python，請務必在安裝程式的 [進階選項] 下，選取 [下載偵錯符號] 和 [下載偵錯二進位檔案]。 這個選項可確保如果您選擇進行偵錯組建，您可以使用必要的偵錯程式庫。

## <a name="create-the-python-application"></a>建立 Python 應用程式

1. **選取 [** 檔案  >  **新增**  >  **專案**]，在 Visual Studio 中建立新的 Python 專案。 搜尋 Python、選取 [Python 應用程式] 範本、提供適合的名稱和位置，並選取 [確定]。

1. 使用 C++ 需要您使用 32 位元 Python 解譯器 (建議使用 Python 3.6 或更新版本)。 在 Visual Studio 的 [方案總管] 視窗中，展開專案節點，然後展開 [Python 環境] 節點。 如果您看到預設值是 32 位元環境 (粗體或標示為 [全域預設值])，請依照[針對專案選取 Python 環境](selecting-a-python-environment-for-a-project.md)上的指示進行。 如果您還未安裝 32 位元解譯器，請參閱[安裝 Python 解譯器](installing-python-interpreters.md)。

1. 在專案的 *.py* 檔案中，貼上下列程式碼，以為雙曲線正切函數的計算進行基準測試 (實作時不使用數學程式庫，以方便比較)。 您可以隨意以手動方式輸入程式碼，來體驗一些 [Python 編輯功能](editing-python-code-in-visual-studio.md)。

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. 在  >  **不進行偵錯工具的情況下**，使用 Debug 啟動來執行程式 (**Ctrl** + **F5**) 以查看結果。 您可以調整 `COUNT` 變數，以變更基準測試的執行花費時間。 基於本逐步解說的目的，請將計數設定為讓基準測試只花約兩秒的時間。

> [!TIP]
> 執行基準測試時，一律使用 **Debug**  >  **Start 而不進行調試** 程式，以避免在 Visual Studio 偵錯工具內執行程式碼時所產生的額外負荷。

## <a name="create-the-core-c-projects"></a>建立核心 C++ 專案

請遵循本節中的指示，建立名為 "superfastcode" 和 "superfastcode2" 的兩個相同 C++ 專案。 稍後您將在每個專案中使用不同的方法，將 C++ 程式碼向 Python 公開。

1. 確定 `PYTHONHOME` 環境變數設定為您要使用的 Python 解譯器。 Visual Studio 中的 C++ 專案依賴這個變數來找出 *python.h* 這類檔案，建立 Python 延伸模組時會使用這些檔案。

1. 以滑鼠右鍵按一下 [方案總管] 中的方案，然後選取 [加入] > [新增專案]。 Visual Studio 解決方案可同時包含 Python 與 C++ 專案 (這是使用 Visual Studio for Python 的好處之一)。

1. 搜尋 "C++"、選取 [空專案]、指定名稱 "superfastcode" (針對第二個專案指定 "superfastcode2")，然後選取 [確定]。

    > [!Tip]
    > 在 Visual Studio 中安裝 **Python 原生開發工具** 後，您便可從 [Python 延伸模組] 範本著手，其已包含此處所述的大多數功能。 不過，在此逐步解說中，從空白專案開始將逐步示範如何建置延伸模組。 只要您了解了程序，此範本就能在您撰寫自己的延伸模組時為您節省時間。

1. 在新專案中建立 C++ 檔案，方法是以滑鼠右鍵按一下 [來源檔案] 節點，然後選取 [加入] > [新增項目]、選取 [C++ 檔案]、將它命名為 `module.cpp`，然後選取 [確定]。

    > [!Important]
    > 必須有具有 *.cpp* 副檔名的檔案，才能在後續步驟開啟 C++ 屬性頁面。

1. 以滑鼠右鍵按一下 [方案總管] 中的 C++ 專案，然後選取 [屬性]。

1. 在出現的 [屬性頁] 對話方塊上方，將 [組態] 設定為 [所有組態]，將 [平台] 設定為 [Win32]。

1. 依下表所述設定特定的屬性，然後選取 [確定]。

    | 索引標籤 | 屬性 | 值 |
    | --- | --- | --- |
    | **一般** | **一般**  > **目標名稱** | 依您希望來指定模組名稱，用 `from...import` 陳述式從 Python 中參考它。 為 Python 定義模組時，會在 C++ 中使用相同名稱。 如果想用專案名稱當作模組名稱，請保留預設值 **$(ProjectName)**。 |
    | | **一般**  > **目標擴充** 功能 | **.pyd** |
    | | **專案預設值**  > 設定 **類型** | **動態程式庫 (.dll)** |
    | **C/C + +**  > **一般** | **其他 Include 目錄** | 視情況為您的安裝新增 Python *include* 資料夾，例如 `c:\Python36\include`。  |
    | **C/C + +**  > **預處理器** | **前置處理器定義** | **僅限 CPython**：將 `Py_LIMITED_API;` 新增至字串的開頭 (包括分號)。 此定義會限制您可以從 Python 呼叫的某些功能，並使程式碼更容易在不同版本的 Python 之間移植。 如果您使用 PyBind11，請勿新增這個定義，否則您將會看到建置錯誤。 |
    | **C/C + +**  > 程式 **代碼產生** | **執行階段程式庫** | **多執行緒 DLL (/md)** (請參閱以下警告)  |
    | **連結器**  > **一般** | **其他程式庫目錄** | 視您的安裝新增適當的 Python *libs* 資料夾並包含 *.lib* 檔案，例如 `c:\Python36\libs`。 (請務必指向包含 *.lib* 檔案的 *libs* 資料夾，而「不是」包含 *.py* 檔案的 *Lib* 資料夾。) |

    > [!Tip]
    > 如果在專案 [屬性] 中沒有看到 [C/C++] 索引標籤，這是因為專案不包含它識別為 C/C++ 原始程式檔的任何檔案。 如果您建立原始程式檔，而沒有 *.c* 或 *.cpp* 副檔名，便可能發生此情形。 例如，如果您 `module.coo` 不小心 `module.cpp` 在先前的 [新專案] 對話方塊中輸入而不是，則 Visual Studio 會建立檔案，但不會將檔案類型設定為 [C/c + + 程式碼]，這就是啟動 c/c + + 屬性索引標籤的專案。即使您將檔案重新命名，也會保留這類禮貌語氣問題 `.cpp` 。 若要適當地設定檔案類型，請以滑鼠右鍵按一下 **方案總管** 中的檔案，選取 [ **屬性**]，然後將 [  **檔案類型** ] 設定為 **C/c + + 程式碼**。

    > [!Warning]
    > 一律將 **C/c + +** 程式  >  **代碼產生**  >  **運行** 時間程式庫選項設定為 **多執行緒 DLL (/md)**，即使是針對 debug 設定，因為這項設定是用來建立非 debug Python 二進位檔的設定。 使用 CPython 時，如果您 **(/MDd) 選項設定多執行緒的偵錯工具 DLL** ，建立 **Debug** 設定會產生錯誤 **C1189： Py_LIMITED_API 與 Py_DEBUG、Py_TRACE_REFS 和 Py_REF_DEBUG 不相容**。 此外，如果您移除 `Py_LIMITED_API` (其對 CPython 為必要項，但對 PyBind11 則不是) 以避免發生建置錯誤，Python 會在嘗試匯入模組時當機。 (當機會發生在 DLL 的 `PyModule_Create` 呼叫內，如稍後所述，輸出訊息為「Python 嚴重錯誤︰PyThreadState_Get︰沒有目前的執行緒」。)
    >
    > /MDd 選項可用來建立 Python debug 二進位檔 (例如 *python_d.exe*) ，但針對延伸模組 DLL 選取它仍會導致組建錯誤 `Py_LIMITED_API` 。

1. 以滑鼠右鍵按一下 c + + 專案，然後選取 [ **建立** ] 以測試您的設定 (**Debug** 和 **Release**) 。 *.pyd* 檔案位於 **Debug** 和 **Release** 下的 **solution** 資料夾，而不是 C++ 專案資料夾本身。

1. 將下列程式碼加入 C++ 專案的 *module.cpp* 檔案︰

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

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. 重新建置 C++ 專案，確認您的程式碼正確。

1. 如果您尚未這麼做，請重複上述步驟，以建立名為 "superfastcode2" 且具有相同內容的第二個專案。

## <a name="convert-the-c-projects-to-extensions-for-python"></a>將 C++ 專案轉換成適用於 Python 的延伸模組

若要讓 C++ DLL 成為適用於 Python 的延伸模組，您要先修改匯出的方法以和 Python 類型互動。 然後，新增匯出模組的函式，以及模組方法的定義。

下列各節說明如何使用 CPython 延伸模組和 PyBind11 執行這些步驟。

### <a name="cpython-extensions"></a>CPython 延伸模組

如需在本節中為 Python 3.x 所顯示之項目的詳細資訊，請參閱 [Python/C API 參考手冊](https://docs.python.org/3/c-api/index.html)，特別是 python.org 上的[模組物件](https://docs.python.org/3/c-api/module.html) (請記得在右上角的下拉式控制項選取您的 Python 版本，以檢視正確的文件)。

如果您正在使用 Python 2.7，請改為參閱 python.org 的[使用 C 或 C++ 延伸 Python 2.7](https://docs.python.org/2.7/extending/extending.html) 和[將延伸模組移植到 Python 3](https://docs.python.org/2.7/howto/cporting.html)。

1. 在 *module.cpp* 頂端，包含 *Python.h*：

    ```cpp
    #include <Python.h>
    ```

1. 修改 `tanh_impl` 方法以接受並傳回 Python 類型 (即 `PyObject*`)︰

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. 新增結構，定義 C++ `tanh_impl` 函式如何向 Python 呈現：

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. 新增可定義模組的結構，因為您想要在 Python 程式碼中參照它，特別是使用 `from...import` 陳述式時。  (使其符合 [設定 **屬性**  >  **一般**  >  **目標名稱**] 下專案屬性中的值。 ) 在下列範例中，"superfastcode" 模組名稱表示您可以 `from superfastcode import fast_tanh` 在 Python 中使用，因為 `fast_tanh` 是在中定義 `superfastcode_methods` 。 C + + 專案內部的 (檔案名（例如 *module*）為不重要。 ) 

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. 新增 Python 在載入模組時呼叫的方法（必須命名 `PyInit_<module-name>` ），其中 &lt; 模組名稱 &gt; 完全符合 c + + 專案的 **一般**  >  **目標名稱** 屬性 (也就是，它會比對專案) 所建立的 *>.pyd* 檔案名。

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. 將目標設定設為 [ **發行** ]，然後再次建立 c + + 專案以驗證您的程式碼。 如果您遇到錯誤，請參閱下列[疑難排解](#troubleshooting)一節。

### <a name="pybind11"></a>PyBind11

如果您已完成上一節中的步驟，您肯定注意到您使用了許多樣板程式碼，來建立 C++ 程式碼的必要模組結構。 PyBind11 透過 C++ 標頭檔的巨集簡化此程序，該巨集能以少上許多的程式碼達到相同的結果。 如需本節中所示內容的背景，請參閱 [PyBind11 基本知識](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com)。

1. 使用 pip 安裝 PyBind11：`pip install pybind11` 或 `py -m pip install pybind11`。

1. 在 *module.cpp* 頂端，包含 *pybind11.h*：

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. 在 *module.cpp* 底部，使用 `PYBIND11_MODULE` 巨集來定義 C++ 函式的進入點：

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. 將目標組態設定為 [發行]，並建置 C++ 專案以驗證您的程式碼。 如果您遇到錯誤，請參閱下一節的疑難排解內容。

### <a name="troubleshooting"></a>疑難排解

C++ 模組可能因為下列原因而無法編譯：

- 找不到 *Python.h* (「E1696：無法開啟來源檔案 "Python.h"」/或「C1083：無法開啟 include 檔案："Python.h"：沒有這種檔案或目錄」)，請驗證專案屬性中 [C/C++] > [一般] > [其他 Include 目錄] 的路徑指向您 Python 安裝的 *include* 資料夾。 請參閱[建立 Core C++ 專案](#create-the-core-c-projects)下的步驟 6。

- 找不到 python 程式庫：確認專案屬性中 [**連結器**  >  **一般** 其他程式庫目錄] 中的路徑  >  指向您的 Python 安裝的連結 **庫** 資料夾。 請參閱[建立 Core C++ 專案](#create-the-core-c-projects)下的步驟 6。

- 與目標架構相關的連結器錯誤：變更 C++ 目標的專案結構使符合您的 Python 安裝結構。 例如，如果您的 C++ 專案以 x64 為目標，但是您的 Python 安裝為 x86，請將 C++ 專案變更為以 x86 為目標。

## <a name="test-the-code-and-compare-the-results"></a>測試程式碼，並比較結果

現在您已將 DLL 結構化成為 Python 延伸模組，您可以從 Python 專案參考它們、匯入模組，並使用其方法。

### <a name="make-the-dll-available-to-python"></a>讓 Python 使用 DLL

有兩種方式，可讓 Python 使用 DLL。

如果 Python 專案和 C++ 專案都在相同的解決方案中，第一種方法就會起作用。 移至 **方案總管**，以滑鼠右鍵按一下 Python 專案中的 [ **參考** ] 節點，然後選取 [ **加入參考**]。 在出現的對話方塊中，依序選取 [專案] 索引標籤、[superfastcode] 和 [superfastcode2] 專案，然後按一下 [確定]。

![將參考新增至 superfastcode 專案](media/cpp-add-reference.png)

在後續步驟中描述的另一種方法，會將模組安裝在全域 Python 環境中，將它也提供給其他 Python 專案使用。 (這樣做，通常需要您在 Visual Studio 2017 15.5 版及較舊版本中重新整理該環境的 IntelliSense 完成資料庫。 從環境移除模組時，也需要重新整理。)

1. 如果您使用 Visual Studio 2017 或更新版本，請執行 Visual Studio 安裝程式，然後依序選取 [修改]、[個別元件] > [編譯器、建置工具和執行階段] > [Visual C++ 2015.3 v140 工具組]。 此步驟之所以必要，是因為 Python (適用於 Windows) 本身是使用 Visual Studio 2015 (14.0 版) 來建置，因此在透過此處所述方法建置延伸模組時，Python 預期要能使用這些工具 。 (請注意，您可能需要安裝 32 位元版本的 Python 並將 DLL 的目標設成 Win32 而不是 x64。)

1. 以滑鼠右鍵按一下 C++ 專案、建立名為 *setup.py* 的檔案，然後選取 [新增] > [新增項目]。 接著，選取 [C++ 檔案 (.cpp)]，將檔案命名為 `setup.py`，並選取 [確定] (使用 *.py* 副檔名命名檔案時，即可讓 Visual Studio 將其辨識為 Python，即使使用 C++ 檔案範本亦同)。 當檔案出現在編輯器中時，以適合延伸模組方法的方式，將下列程式碼貼入檔案中︰

    **CPython 延伸模組 (superfastcode 專案)：**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    如需此指令碼的文件，請參閱[建置 C 和 C++ 延伸模組](https://docs.python.org/3/extending/building.html) (python.org)。

    **PyBind11 (superfastcode2 專案)：**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. 從命令列使用 *setup.py* 程式碼時，其會指示 Python 使用 Visual Studio 2015 C++ 工具組建置延伸模組。 開啟提升權限的命令提示字元、巡覽至包含 C++ 專案的資料夾 (即包含 *setup.py* 的資料夾)，然後輸入下列命令︰

    ```command
    pip install .
    ```

    或者：

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>從 Python 呼叫 DLL

您已如上一節中所述，讓 DLL 可供 Python 使用之後，您現在可以從 Python 程式碼呼叫 `superfastcode.fast_tanh` 和 `superfastcode2.fast_tanh2` 函式，並比較其效能與 Python 實作：

1. 在您的 *.py* 檔案中新增下列幾行，呼叫從 DLL 匯出的方法，並顯示其輸出：

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. 執行 python 程式 (**Debug**  >  **啟動，而不需調試** 程式或 **Ctrl** + **F5**) 並觀察 c + + 常式執行的速度比 Python 的執行速度大約五到20倍。 一般輸出會以下列形式呈現：

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    如果已停用 [ **啟動但不含調試** 程式] 命令，請以滑鼠右鍵按一下 **方案總管** 中的 Python 專案，然後選取 [ **設定為啟始專案**]。

1. 您可以嘗試增加 `COUNT` 變數，讓差異更加明顯。 C + + 模組的 **debug** 組建也會比 **發行** 組建慢，因為 **debug** 組建較不優化，而且包含各種錯誤檢查。 您可以自行切換這些組態以進行比較。

> [!NOTE]
> 在輸出中，您可以看到 PyBind11 延伸模組速度不如 CPython 延伸模組，雖然仍明顯比直接的 Python 實作快。 差異是由於 PyBind11 為了大幅簡化 C++ 介面所造成每次呼叫時的少量額外負荷。 這個每次呼叫時的差異實際上很微不足道：因為測試程式碼會呼叫延伸模組函式 500,000 次，所以您在這裡看到的結果大幅增強了該額外負荷！ C++ 函式通常會比此處使用的一般 `fast_tanh[2]` 方法多做許多工作，在此情況下，額外負荷並不重要。 不過，如果您實作可能每秒呼叫數千次的方法，使用 CPython 方法可能導致效能比 PyBind11 更佳。

## <a name="debug-the-c-code"></a>偵錯 C++ 程式碼

Visual Studio 可支援同時偵錯 Python 和 C++ 程式碼。 本節將逐步引導完成使用 **superfastcode** 專案的程序；其步驟與 **superfastcode2** 專案的步驟相同。

1. 在 [方案總管] 中以滑鼠右鍵按一下 Python 專案、依序選取 [屬性]、[偵錯] 索引標籤，然後選取 [偵錯] > [啟用機器碼偵錯] 選項。

    > [!Tip]
    > 當您啟用機器碼的偵錯工具時，Python 輸出視窗可能會在程式完成時立即消失，而不會讓您正常 **按下任何鍵以繼續** 暫停。 若要強制暫停，請在 `-i` 啟用機器碼偵錯工具時，將選項新增至 [偵錯工具] 索引標籤上的 [**執行**  >  **解譯器引數**] 欄位。  此引數會在程式碼完成之後，將 Python 解譯器放入互動模式中，此時它會等候您按下 **Ctrl** + **Z**  >  **enter** 結束。 (或者，如果您不介意修改 Python 程式碼，可以在程式結尾新增 `import os` 和 `os.system("pause")` 陳述式。 此程式碼會複製原始暫停提示字元。)

1. 選取  >  [**儲存** 盤案] 以儲存屬性變更。

1. 將 [組建設定] 設定為 [Visual Studio] 工具列中的 [ **Debug** ]。

    ![將組建組態設為 [偵錯]](media/cpp-set-debug.png)

1. 在偵錯工具中執行程式碼通常會花較長時間，因此您可以將 *.py* 檔案中的 `COUNT` 變數改為少 5 倍的值 (例如，將它從 `500000` 變更為 `100000`)。

1. 在您的 C++ 程式碼中，於 `tanh_impl` 方法的第一行設定中斷點，然後啟動偵錯工具 (**F5** 或 [偵錯] > [開始偵錯])。 偵錯工具即會在呼叫該程式碼時停止。 如果未叫用中斷點，請檢查設定是否已設定為 [ **Debug** ]，而且您已儲存專案 (在啟動偵錯工具) 時不會自動發生。

    ![在 C++ 程式碼的中斷點處停止](media/cpp-debugging.png)

1. 此時您可以逐步執行 C++ 程式碼、檢查變數等等。 [同時針對 Python 與 C++ 程式碼進行偵錯](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)中詳述這些功能。

## <a name="alternative-approaches"></a>替代方法

有各種方式可以建立 Python 延伸模組，如下表所述。 CPython 及 PyBind11 的前兩個項目已在本文中討論。

| 方法 | 老式 | 代表使用者 | 正面意見 | 反面意見 |
| --- | --- | --- | --- | --- |
| 適用於 CPython 的 C/C++ 延伸模組 | 1991 | 標準程式庫 | [大量文件與教學課程](https://docs.python.org/3/c-api/)。 完全控制。 | 編譯、可攜性、參考管理。 高度 C 知識。 |
| [PyBind11](https://github.com/pybind/pybind11) (建議用於 c + +)  | 2015 |  | 輕量型、僅限標頭的程式庫，適合建立現有 C++ 程式碼的 Python 繫結。 低相依性。 PyPy 相容性。 | 較新穎、較不成熟。 大量使用 C++11 功能。 支援編譯器的簡短清單 (包含 Visual Studio)。 |
| Cython (建議用於 C) | 2007 | [gevent](https://www.gevent.org/)、[kivy](https://kivy.org/) | 類似 Python。 高度成熟。 高效能。 | 編譯、新的語法和新的工具鏈。 |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | 幾乎可搭配每種 C++ 編譯器使用。 | 大型且複雜的程式庫套件，包含許多舊型編譯器的因應措施。 |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 不需編譯、廣泛可用。 | 存取與變更 C 結構麻煩又容易出錯。 |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 一次產生許多語言的繫結。 | 如果 Python 是唯一的目標，負荷會過大。 |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/)、[pypy](https://pypy.org/) | 輕鬆整合、PyPy 相容性。 | 較新穎、較不成熟。 |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | 類似於使用 C++ 的 cffi。 | 較新，搭配 VS 2017 使用時可能會有一些問題。 |

## <a name="see-also"></a>另請參閱

您可於 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) 找到此逐步解說的完整範例。
