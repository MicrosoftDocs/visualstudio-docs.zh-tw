---
title: 撰寫適用於 Python 的 C++ 延伸模組
description: 使用 Visual Studio、CPython 和 PyBind11 建立適用於 Python 的 C++ 延伸模組逐步解說，包括混合模式偵錯。
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 866b588b8b46477b397cda92076780d1955cfa83
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848301"
---
# <a name="create-a-c-extension-for-python"></a>建立適用於 Python 的 C++ 延伸模組

以 C++ (或 C) 撰寫的模組通常用於延伸 Python 解譯器的功能，以及啟用低階作業系統功能的存取。 有三個主要類型的模組︰

- 加速器模組︰因為 Python 是解譯的語言，可以用 C++ 撰寫特定程式碼以獲得更高的效能。
- 包裝函式模組：向 Python 程式碼公開現有的 C/C++ 介面，或公開來自 Python、容易使用且更具「Python 風格」的 API。
- 低層級的系統存取模組：建立用來存取 `CPython` 執行時間、作業系統或基礎硬體的較低層級功能。

本文將逐步引導您建立的 c + + 延伸模組 `CPython` ，以計算雙曲正切函數，並從 Python 程式碼呼叫它。 常式先以 Python 實作，以示範用 C++ 實作相同常式時的相對效能改善。

本文也會示範兩種方式，讓 Python 可使用 C++：

- `CPython` [Python 檔](https://docs.python.org/3/c-api/)中所述的標準延伸模組
- [PyBind11](https://github.com/pybind/pybind11)，針對 C++ 11 建議使用，因為其單純性。

您可於 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) 找到此逐步解說的完整範例。

## <a name="prerequisites"></a>必要條件

- 已安裝 **Python 開發** 工作負載的 Visual Studio 2017 或更新版本，包括 **python 原生開發工具**，這些工具引進了原生擴充功能所需的 c + + 工作負載和工具組。

    ![選取 Python 原生開發工具選項](media/cpp-install-native.png)

    > [!Tip]
    > 安裝 [資料科學和分析應用程式] 工作負載時，預設也會包含 Python 和 [Python 原生開發工具] 選項。

如需安裝選項的詳細資訊，請參閱 [安裝 Visual Studio 的 Python 支援](installing-python-support-in-visual-studio.md)。 如果您個別安裝 Python，請務必在其安裝程式中選取 [ **Advanced Options** ] 下的 [**下載偵錯工具符號**]。 您必須要有此選項，才能在您的 Python 程式碼和機器碼之間使用混合模式的偵錯工具。

## <a name="create-the-python-application"></a>建立 Python 應用程式

1. **選取 [** 檔案  >  **新增**  >  **專案**]，在 Visual Studio 中建立新的 Python 專案。 搜尋 "Python"，選取 [ **Python 應用程式** ] 範本，並為其提供您選擇的名稱和位置，然後選取 **[確定]**。

1. 在專案的 *.py* 檔案中，貼上下列程式碼 (或手動輸入，以體驗) 的部分 [Python 編輯功能](editing-python-code-in-visual-studio.md) 。 這段程式碼會計算雙曲正切函數，而不使用 math 程式庫，而我們將使用原生擴充功能來加速。

    > [!Tip]
    > 在以 c + + 重寫之前，以純 Python 撰寫您的程式碼。 如此一來，您就可以更輕鬆地檢查機器碼是否正確

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

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

請遵循本節中的指示，建立名為 "superfastcode" 和 "superfastcode2" 的兩個相同 C++ 專案。 稍後，您將在每個專案中使用兩個不同的方法，將 c + + 程式碼公開至 Python。

1. 以滑鼠右鍵按一下 [方案總管] 中的方案，然後選取 [加入] > [新增專案]。 Visual Studio 解決方案可同時包含 Python 與 C++ 專案 (這是使用 Visual Studio for Python 的好處之一)。

1. 搜尋 "C++"、選取 [空專案]、指定名稱 "superfastcode" (針對第二個專案指定 "superfastcode2")，然後選取 [確定]。

    > [!Tip]
    > 在 Visual Studio 中安裝 **Python 原生開發工具** 後，您便可從 [Python 延伸模組] 範本著手，其已包含此處所述的大多數功能。 不過，在此逐步解說中，從空白專案開始將逐步示範如何建置延伸模組。 只要您了解了程序，此範本就能在您撰寫自己的延伸模組時為您節省時間。

1. 在新專案中建立 C++ 檔案，方法是以滑鼠右鍵按一下 [來源檔案] 節點，然後選取 [加入] > [新增項目]、選取 [C++ 檔案]、將它命名為 `module.cpp`，然後選取 [確定]。

    > [!Important]
    > 必須有具有 *.cpp* 副檔名的檔案，才能在後續步驟開啟 C++ 屬性頁面。

1. 如果您使用的是64位的 Python 執行時間，請使用主工具列中的下拉式功能表來啟用 **x64** 設定。 若為32位的 Python 執行時間，請啟用 **Win32** 設定。

1. 以滑鼠右鍵按一下 [方案總管] 中的 C++ 專案，然後選取 [屬性]。 [設定] **的值應該是** [作用中] **([Debug])** 而且 **平臺** 會根據您在上一個步驟中所做的選擇，使用 **(x64)** 或作用中 **(Win32)** 。

    > [!Tip]
    > 針對您自己的專案，您會想要設定 Debug 和 Release 設定。 在此，我們只會設定 Debug 設定，並將它設定為使用的 *發行* 組建 `CPython` ，以停用 c + + 執行時間的某些偵錯工具，包括判斷提示。 使用 `CPython` *debug* 二進位檔 (`python_d.exe`) 將需要不同的設定。

1. 依下表所述設定特定的屬性，然後選取 [確定]。
    ::: moniker range=">=vs-2019"
    | 索引標籤 | 屬性 | 值 |
    | --- | --- | --- |
    | **一般** | **一般** > **目標名稱** | 依您希望來指定模組名稱，用 `from...import` 陳述式從 Python 中參考它。 為 Python 定義模組時，會在 C++ 中使用相同名稱。 如果想用專案名稱當作模組名稱，請保留預設值 **$(ProjectName)**。 |
    | | **Advanced** >**目標副檔名** | **.pyd** |
    | | **專案預設值** > **設定類型** | **動態程式庫 (.dll)** |
    | **C/C++** > **一般** | **其他 Include 目錄** | 視情況為您的安裝新增 Python *include* 資料夾，例如 `c:\Python36\include`。  |
    | **C/C++** > **前置處理器** | **前置處理器定義** | **僅限 CPython**：將 `Py_LIMITED_API;` 新增至字串的開頭 (包括分號)。 此定義會限制您可以從 Python 呼叫的某些功能，並使程式碼更容易在不同版本的 Python 之間移植。 如果您使用 PyBind11，請勿新增這個定義，否則您將會看到建置錯誤。 |
    | **C/C++** > **程式碼產生** | **執行階段程式庫** | **多執行緒 DLL (/md)** (請參閱以下警告)  |
    | **連結器** > **一般** | **其他程式庫目錄** | 視您的安裝新增適當的 Python *libs* 資料夾並包含 *.lib* 檔案，例如 `c:\Python36\libs`。 (請務必指向包含 *.lib* 檔案的 *libs* 資料夾，而「不是」包含 *.py* 檔案的 *Lib* 資料夾。) |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | 索引標籤 | 屬性 | 值 |
    | --- | --- | --- |
    | **一般** | **一般** > **目標名稱** | 依您希望來指定模組名稱，用 `from...import` 陳述式從 Python 中參考它。 為 Python 定義模組時，會在 C++ 中使用相同名稱。 如果想用專案名稱當作模組名稱，請保留預設值 **$(ProjectName)**。 針對 `python_d.exe` ，加入 `_d` 至名稱的結尾。 |
    | | **一般** > **目標擴充功能** | **.pyd** |
    | | **專案預設值** > **設定類型** | **動態程式庫 (.dll)** |
    | **C/C++** > **一般** | **其他 Include 目錄** | 視情況為您的安裝新增 Python *include* 資料夾，例如 `c:\Python36\include`。  |
    | **C/C++** > **前置處理器** | **前置處理器定義** | 如果有的話，請將 **_DEBUG** 值變更為 **NDEBUG**，以符合的非 DEBUG 版本 `CPython` 。 使用時 (`python_d.exe` ，請保持不變。 )  |
    | **C/C++** > **程式碼產生** | **執行階段程式庫** | **多執行緒 DLL (/md)** 與的非 debug 版本相符 `CPython` 。 使用時 (`python_d.exe` ，請保持不變。 )  |
    | **連結器** > **一般** | **其他程式庫目錄** | 視您的安裝新增適當的 Python *libs* 資料夾並包含 *.lib* 檔案，例如 `c:\Python36\libs`。 (請務必指向包含 *.lib* 檔案的 *libs* 資料夾，而「不是」包含 *.py* 檔案的 *Lib* 資料夾。) |
    ::: moniker-end
    
    > [!Tip]
    > 如果在專案 [屬性] 中沒有看到 [C/C++] 索引標籤，這是因為專案不包含它識別為 C/C++ 原始程式檔的任何檔案。 如果您建立原始程式檔，而沒有 *.c* 或 *.cpp* 副檔名，便可能發生此情形。 例如，如果您 `module.coo` 不小心 `module.cpp` 在先前的 [新專案] 對話方塊中輸入而不是，則 Visual Studio 會建立檔案，但不會將檔案類型設定為 [C/c + + 程式碼]，這就是啟動 c/c + + 屬性索引標籤的專案。即使您將檔案重新命名，也會保留這類禮貌語氣問題 `.cpp` 。 若要適當地設定檔案類型，請以滑鼠右鍵按一下 **方案總管** 中的檔案，選取 [ **屬性**]，然後將 [  **檔案類型** ] 設定為 **C/c + + 程式碼**。

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

下列各節說明如何使用擴充功能和 PyBind11 執行這些步驟 `CPython` 。

### <a name="cpython-extensions"></a>CPython 延伸模組

如需本節所示內容的詳細背景，請參閱 python.org 上的 [python/C API 參考手冊](https://docs.python.org/3/c-api/index.html) 和特別的 [模組物件](https://docs.python.org/3/c-api/module.html) (請記得從右上角的下拉式控制項中選取您的 python 版本，以查看正確的檔) 。

1. 在 *module.cpp* 頂端，包含 *Python.h*：

    ```cpp
    #include <Python.h>
    ```

1. 修改 `tanh_impl` 方法以接受並傳回 Python 類型 (即 `PyObject*`)︰

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. 新增結構，定義 C++ `tanh_impl` 函式如何向 Python 呈現：

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
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

1. 重新建置 C++ 專案，以驗證您的程式碼。 如果您遇到錯誤，請參閱下列[疑難排解](#troubleshooting)一節。

### <a name="pybind11"></a>PyBind11

如果您已完成上一節中的步驟，您肯定注意到您使用了許多樣板程式碼，來建立 C++ 程式碼的必要模組結構。 PyBind11 透過 C++ 標頭檔的巨集簡化此程序，該巨集能以少上許多的程式碼達到相同的結果。 如需本節中所示內容的背景，請參閱 [PyBind11 基本知識](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com)。

1. 使用 pip 安裝 PyBind11：`pip install pybind11` 或 `py -m pip install pybind11`。  (另外，您可以使用 [Python 環境] 視窗進行安裝，然後在下一個步驟中使用其 [在 Powershell 中開啟] 命令。 ) 

1. 在相同的終端機中，執行 `python -m pybind11 --includes` 或 `py -m pybind11 --includes` 。 這會列印您應該新增至專案 **C/c + +**  >  **[一般**  >  **其他 Include 目錄**] 屬性的路徑清單 (移除 `-I` 前置詞（如果有的話）) 。

1. 在新的 *模組 .cpp* 頂端，不包含上一節中的任何變更，包括 *pybind11*：

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

1. 建立 c + + 專案以驗證您的程式碼。 如果您遇到錯誤，請參閱下一節的疑難排解內容。

### <a name="troubleshooting"></a>疑難排解

C++ 模組可能因為下列原因而無法編譯：

- 找不到 *Python.h* (「E1696：無法開啟來源檔案 "Python.h"」/或「C1083：無法開啟 include 檔案："Python.h"：沒有這種檔案或目錄」)，請驗證專案屬性中 [C/C++] > [一般] > [其他 Include 目錄] 的路徑指向您 Python 安裝的 *include* 資料夾。 請參閱[建立 Core C++ 專案](#create-the-core-c-projects)下的步驟 6。

- 找不到 python 程式庫：確認專案屬性中 [**連結器**  >  **一般** 其他程式庫目錄] 中的路徑  >  指向您的 Python 安裝的連結 **庫** 資料夾。 請參閱[建立 Core C++ 專案](#create-the-core-c-projects)下的步驟 6。

- 與目標架構相關的連結器錯誤：變更 C++ 目標的專案結構使符合您的 Python 安裝結構。 例如，如果您是以 c + + **專案為目標** ，但您的 Python 安裝是64位，請將 c + + 專案變更為 **x64**。

## <a name="test-the-code-and-compare-the-results"></a>測試程式碼，並比較結果

現在您已將 DLL 結構化成為 Python 延伸模組，您可以從 Python 專案參考它們、匯入模組，並使用其方法。

### <a name="make-the-dll-available-to-python"></a>讓 Python 使用 DLL

有兩種方式，可讓 Python 使用 DLL。

如果 Python 專案和 C++ 專案都在相同的解決方案中，第一種方法就會起作用。 移至 **方案總管**，以滑鼠右鍵按一下 Python 專案中的 [ **參考** ] 節點，然後選取 [ **加入參考**]。 在出現的對話方塊中，依序選取 [專案] 索引標籤、[superfastcode] 和 [superfastcode2] 專案，然後按一下 [確定]。

![將參考新增至 superfastcode 專案](media/cpp-add-reference.png)

下列步驟中所述的替代方法，會在您的 Python 環境中安裝模組，讓其他 Python 專案也可以使用。 如需更完整的檔，請造訪 [ **setuptools** 專案](https://setuptools.readthedocs.io/)。

1. 以滑鼠右鍵按一下 C++ 專案、建立名為 *setup.py* 的檔案，然後選取 [新增] > [新增項目]。 接著，選取 [C++ 檔案 (.cpp)]，將檔案命名為 `setup.py`，並選取 [確定] (使用 *.py* 副檔名命名檔案時，即可讓 Visual Studio 將其辨識為 Python，即使使用 C++ 檔案範本亦同)。 當檔案出現在編輯器中時，以適合延伸模組方法的方式，將下列程式碼貼入檔案中︰

    **`CPython` 擴充功能 (superfastcode 專案) ：**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11` (superfastcode2 專案) ：**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. 在 c + + 專案中建立名為 *pyproject* 的第二個檔案，並在其中貼上下列程式碼。

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. 若要建立延伸模組，請以滑鼠右鍵按一下 [開啟 *pyproject* ] 索引標籤，然後選取 [複製完整路徑] (我們將會從路徑中刪除 *pyproject. >gopkg.toml* 名稱，再使用) 。

1. 在方案總管中，以滑鼠右鍵按一下作用中的 Python 環境，然後選取 [ *管理 Python 套件*]。

    > [!Tip]
    > 如果您已經安裝封裝，您會看到它列在這裡。 按一下 [X] 將它卸載後再繼續。

1. 將複製的路徑貼到 [搜尋] 方塊 `pyproject.toml` 中，然後從結尾刪除。 然後按 Enter 鍵，從該目錄進行安裝。

    > [!Tip]
    > 如果因為許可權錯誤而導致安裝失敗，請新增， `--user` 然後再試一次命令。


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

1. 您可以嘗試增加 `COUNT` 變數，讓差異更加明顯。 C + + 模組的 **debug** 組建也會比 **發行** 組建慢，因為 **debug** 組建較不優化，而且包含各種錯誤檢查。 您可以在這些設定之間切換以進行比較 (但請記得從先前的版本中，更新 **發行** 設定) 的屬性。

在輸出中，您可能會看到 PyBind11 延伸模組的速度不如擴充的快 `CPython` ，不過它應該比單純的 Python 更快。 這項差異主要是因為我們使用了 `METH_O` 不支援多個參數、參數名稱或關鍵字引數的呼叫。 PyBind11 會產生稍微更複雜的程式碼，以提供更多類似 Python 的介面給呼叫端，但由於測試程式碼會呼叫函數500000次，因此結果可能會大幅增強該額外負荷！

我們可以藉由將迴圈移至機器碼，來更進一步地減少額外負荷 `for` 。 這會涉及使用 [反覆運算器通訊協定](https://docs.python.org/c-api/iter.html) (或 PyBind11's `py::iterable` 類型，讓 [函數參數](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) 處理每個專案。 移除 Python 與 c + + 之間重複的轉換，是減少處理順序所花費時間的有效方式。

### <a name="troubleshooting"></a>疑難排解

如果您在 `ImportError` 嘗試匯入模組時收到，可能是因為下列其中一個問題所造成：

* 透過專案參考建立時，請確定您的 c + + 專案屬性符合為 Python 專案啟用的 Python 環境，特別是包含和程式庫目錄。

* 確定您的輸出檔案已命名 `superfastcode.pyd` 。 不同的名稱或副檔名將會導致無法匯入。

* 如果您使用 *setup.py* 檔案安裝您的模組，請確認您已在針對 python 專案啟用的 python 環境中執行 *pip* 命令。 展開方案總管中的 Python 環境應該會顯示的專案 `superfastcode` 。

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

有各種方式可以建立 Python 延伸模組，如下表所述。 和的前兩個專案是本文中已討論過的 `CPython` `PyBind11` 內容。

| 方法 | 老式 | 代表使用者 | 
| --- | --- | --- |
| 的 c/c + + 延伸模組模組 `CPython` | 1991 | 標準程式庫 | 
| [PyBind11](https://github.com/pybind/pybind11) (建議用於 c + +)  | 2015 |  |
| [Cython](https://cython.org) (建議用於 C)  | 2007 | [gevent](https://www.gevent.org/)、[kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [cryptography](https://cryptography.io/)、[pypy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>另請參閱

您可於 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) 找到此逐步解說的完整範例。
