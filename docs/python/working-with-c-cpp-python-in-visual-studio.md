---
title: 撰寫適用於 Python 的 C++ 延伸模組
description: 本文將逐步引導您瞭解如何使用 Visual Studio、CPython 和 PyBind11 （包括混合模式的偵錯工具）來建立適用于 Python 的 c + + 擴充功能。
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973436"
---
# <a name="create-a-c-extension-for-python"></a>建立適用於 Python 的 C++ 延伸模組

以 c + + (或 C) 撰寫的模組通常用來擴充 Python 解譯器的功能。 它們也可用來存取低層級的作業系統功能。 

模組分為三種主要類型：

- **加速器模組**：由於 Python 是一種解讀的語言，因此您可以在 c + + 中撰寫加速器模組，以獲得更高的效能。
- **包裝** 函式模組：這些模組會向 python 程式碼公開現有的 c/c + + 介面，或公開更容易從 python 使用的「PYTHONIC」 API。
- **低層級的系統存取模組**：您可以建立這些模組來存取 `CPython` 執行時間、作業系統或基礎硬體的較低層級功能。

本文將逐步引導您建立的 c + + 延伸模組 `CPython` ，以計算雙曲正切函數，並從 Python 程式碼呼叫它。 常式先以 Python 實作，以示範用 C++ 實作相同常式時的相對效能改善。

本文也會示範兩種讓 c + + 擴充功能可供 Python 使用的方式：

- 使用標準 `CPython` 延伸模組，如 [Python 檔](https://docs.python.org/3/c-api/)中所述。
- 使用 [PyBind11](https://github.com/pybind/pybind11)，我們建議您在 c + + 11 中使用，因為它是簡單的。

您可以在 GitHub 的 [python （範例-vs-cpp-擴充](https://github.com/Microsoft/python-sample-vs-cpp-extension)功能）上找到此逐步解說中的完整範例。

## <a name="prerequisites"></a>必要條件

- Visual Studio 2017 或更新版本，且已安裝 Python 開發工作負載。 工作負載包含 Python 原生開發工具，可帶入原生擴充功能所需的 c + + 工作負載和工具組。

    ![Python 開發選項清單的螢幕擷取畫面，其中反白顯示 Python 原生開發工具選項。](media/cpp-install-native.png)

    > [!NOTE]
    > 當您安裝 **資料科學和分析應用程式** 工作負載時，預設會安裝 Python 和 **python 原生開發工具** 選項。

如需安裝選項的詳細資訊，請參閱 [安裝 Visual Studio 的 Python 支援](installing-python-support-in-visual-studio.md)。 如果您個別安裝 Python，請務必在其安裝程式中選取 [ **Advanced Options** ] 下的 [**下載偵錯工具符號**]。 您必須使用此選項，才能在您的 Python 程式碼和機器碼之間使用混合模式的偵錯工具。

## <a name="create-the-python-application"></a>建立 Python 應用程式

1. **選取 [** 檔案  >  **新增**  >  **專案**]，在 Visual Studio 中建立新的 Python 專案。 搜尋 **python**，選取 [ **python 應用程式** ] 範本，輸入名稱和位置，然後選取 **[確定]**。

1. 在專案的 *.py* 檔案中，貼上下列程式碼。 若要體驗某些 [Python 編輯功能](editing-python-code-in-visual-studio.md)，請嘗試手動輸入程式碼。  

   此程式碼會計算雙曲正切函數，而不使用 math 程式庫，而您將使用原生擴充功能來加速。

    > [!Tip]
    > 在以 c + + 撰寫程式碼之前，以純 Python 撰寫您的程式碼。 如此一來，您就可以更輕鬆地檢查以確定機器碼正確無誤。

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

1. 若要查看結果，請選取 [不使用偵錯工具來  >  **啟動** Debug] 或選取 Ctrl + F5 來執行程式。 

   您可以調整 `COUNT` 變數，以變更基準測試的執行花費時間。 基於本逐步解說的目的，請設定計數，讓基準測試大約需要兩秒鐘的時間。

   > [!TIP]
   > 當您執行基準測試時，請一律使用 **Debug**  >  **啟動，而不進行調試**。 這有助於避免在 Visual Studio 偵錯工具中執行程式碼時所產生的額外負荷。

## <a name="create-the-core-c-projects"></a>建立核心 C++ 專案

遵循本節中的指示，以建立兩個相同的 c + + 專案： *superfastcode* 和 *superfastcode2*。 稍後，您將在每個專案中使用不同的方法，將 c + + 程式碼公開至 Python。

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案，然後選取 [**加入**  >  **新專案**]。 Visual Studio 的解決方案可以同時包含 Python 和 c + + 專案，這是使用 Visual Studio for Python 的優點之一。

1. 在 **c + +** 上搜尋、選取 [ **空白專案**]、為第一個專案指定 **superfastcode** ，或針對第二個專案指定 [ **Superfastcode2** ]，然後選取 **[確定]**。

    > [!Tip]
    > 或者，在 Visual Studio 中安裝 Python 原生開發工具之後，您就可以從 Python 延伸模組範本開始。 此範本已有大部分的現成描述。 
    > 
    > 不過，在此逐步解說中，從空白專案開始將逐步示範如何建置延伸模組。 瞭解程式之後，您可以使用範本來節省撰寫專屬延伸模組的時間。

1. 若要在新專案中建立 c + + 檔案，請以滑鼠右鍵按一下 [**來源** 檔案] 節點，然後選取 [**加入**  >  **新專案**]。

1. 選取 **c + +** 檔案，將它命名為 *.cpp*，然後選取 **[確定]**。

    > [!Important]
    > 必須有具有 *.cpp* 副檔名的檔案，才能在後續步驟開啟 C++ 屬性頁面。

1. 在主要工具列上，使用下拉式功能表來執行下列其中一項：

   * 若為64位的 Python 執行時間，請啟用 **x64** 設定。 
   * 若為32位的 Python 執行時間，請啟用 **Win32** 設定。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 c + + 專案，選取 [ **屬性**]，然後執行下列動作： 

   a. 針對 **[** 設定]，輸入 **Active (Debug)**。  
   b. 針對 [ **平臺**]，根據您在上一個步驟中選取的專案，輸入 **active (X64)** 或 **active (Win32)**。

    > [!NOTE]
    > 當您建立自己的專案時，您會想要設定 *debug* 和 *release* 設定。 在此單元中，您只會設定偵錯工具設定，並將它設定為使用 CPython 的發行組建。 這項設定會停用 c + + 執行時間的某些偵錯工具，包括判斷提示。 使用 CPython debug 二進位檔 (*python_d.exe*) 需要不同的設定。

1. 依照下表所述設定屬性：

    ::: moniker range=">=vs-2019"

    | 索引標籤 | 屬性 | 值 |
    | --- | --- | --- |
    | **一般** | **目標名稱** | 在語句中指定要從 Python 參考的模組名稱 `from...import` 。 當您定義適用于 Python 的模組時，您會在 c + + 程式碼中使用這個相同的名稱。 若要使用專案的名稱做為模組名稱，請保留的預設值 **$\<ProjectName>** 。  針對 `python_d.exe` ，加入 `_d` 至名稱的結尾。 |
    | | **組態類型** | **動態程式庫 (.dll)** |
    | | **Advanced** >**目標副檔名** | **.pyd** |
    | | **專案預設值** > **設定類型** | **動態程式庫 (.dll)** |
    | **C/C++** > **一般** | **其他 Include 目錄** | 為您的安裝新增適當的 Python *include* 資料夾 (例如 `c:\Python36\include`) 。  |
    | **C/C++** > **前置處理器** | **前置處理器定義** | 如果存在，請將 **_DEBUG** 值變更為 **NDEBUG** ，以符合 CPython 的非 DEBUG 版本。 當您使用 *python_d.exe* 時，請將此值維持不變。 |
    | **C/C++** > **程式碼產生** | **執行階段程式庫** | **多執行緒 DLL (/md)** ，以符合 CPython 的非偵錯工具版本。 當您使用 *python_d.exe* 時，請將此值保留為 **多執行緒的 Debug DLL (/MDd)**。 |
    | **連結器** > **一般** | **其他程式庫目錄** | 新增包含 .lib 檔案 *的 Python* 連結 *庫* 資料夾（適用于您的安裝 (例如， *c:\Python36\libs*) ）。 請務必指向包含 *.lib* 檔案的程式庫資料夾，而 *不* 是包含 *.py* 檔案的 *lib* *資料夾。* |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | 索引標籤 | 屬性 | 值 |
    | --- | --- | --- |
    | **一般** | **一般** > **目標名稱** | 在語句中指定要從 Python 參考的模組名稱 `from...import` 。 當您定義適用于 Python 的模組時，您會在 c + + 程式碼中使用這個相同的名稱。 若要使用專案的名稱做為模組名稱，請保留的預設值 **$\<ProjectName>** 。 針對 `python_d.exe` ，加入 `_d` 至名稱的結尾。 |
    | | **一般** > **目標擴充功能** | **.pyd** |
    | | **專案預設值** > **設定類型** | **動態程式庫 (.dll)** |
    | **C/C++** > **一般** | **其他 Include 目錄** | 根據您的安裝，新增 Python *include* 資料夾 (例如， *c:\Python36\include*) 。  |
    | **C/C++** > **前置處理器** | **前置處理器定義** | 如果存在，請將 **_DEBUG** 值變更為 **NDEBUG** ，以符合的非 DEBUG 版本 `CPython` 。 當您使用時 `python_d.exe` ，此值會保持不變。 |
    | **C/C++** > **程式碼產生** | **執行階段程式庫** | **多執行緒 DLL (/md)** 與的非 debug 版本相符 `CPython` 。 當您使用時 `python_d.exe` ，此值會保持不變。 |
    | **連結器** > **一般** | **其他程式庫目錄** | 新增包含 .lib 檔案 *的 Python* 連結 *庫* 資料夾（適用于您的安裝 (例如， *c:\Python36\libs*) ）。 請務必指向包含 *.lib* 檔案的程式庫資料夾，而 *不* 是包含 *.py* 檔案的 *lib* *資料夾。* |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > 如果 [ **c/c + +** ] 索引標籤未顯示在專案屬性中，專案就不會包含它識別為 C/c + + 原始程式檔的任何檔案。 如果您建立不含 *.c* 或 *.cpp* 副檔名的原始檔，就會發生這種情況。 
    > 
    > 例如，如果您不小心在 [新專案] 對話方塊中輸入 *coo* ，而不是稍早在 *模組* 中輸入 .cpp，Visual Studio 會建立檔案，但不會將檔案類型設定為 *c/c + + 程式碼*，這會啟用 [c/c + + 屬性] 索引標籤。即使您重新命名副檔名為 *.cpp* 的檔案，也會保留這類禮貌語氣問題。 
    > 
    > 若要正確設定檔案類型，請在 [ **方案總管** 中，以滑鼠右鍵按一下檔案，然後選取 [ **屬性**]。 然後，在 [ **檔案類型**] 中，選取 **C/c + + 程式碼**。

1. 選取 [確定]。

1. 若要測試您的設定 (*debug* 和 *release*) ，請以滑鼠右鍵按一下 c + + 專案，然後選取 [ **建立**]。 

   您會在 [*方案*] 資料夾中的 [ *Debug* 和 *Release*] 下找到 *>.pyd* 檔案，而不是在 c + + 專案資料夾本身。

1. 在 c + + 專案的 *模組 .cpp* 檔案中，加入下列程式碼：

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

1. 如果您尚未這麼做，請重複上述步驟，使用相同的設定建立名為 *superfastcode2* 的第二個專案。

## <a name="convert-the-c-projects-to-extensions-for-python"></a>將 C++ 專案轉換成適用於 Python 的延伸模組

若要讓 c + + DLL 成為適用于 Python 的延伸模組，您必須先修改匯出的方法以與 Python 類型互動。 然後，新增匯出模組的函式，以及模組方法的定義。

接下來的章節將說明如何使用 CPython 延伸模組和 PyBind11 來執行這些步驟。

### <a name="use-cpython-extensions"></a>使用 CPython 延伸模組

如需本節所示程式碼的詳細背景，請參閱 [Python/C API 參考手冊](https://docs.python.org/3/c-api/index.html) （尤其是 [模組物件](https://docs.python.org/3/c-api/module.html) 頁面）。 請務必在右上方的下拉式清單中選取您的 Python 版本。

1. 在 *模組 .cpp* 檔案的頂端，包含 *Python .h*：

    ```cpp
    #include <Python.h>
    ```

1. 修改 `tanh_impl` 方法以接受並傳回 Python 類型 (也就是 `PyObject*`) ：

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

1. 新增結構來定義您想要在 Python 程式碼中參考的模組，特別是當您使用 `from...import` 語句時。 

   在此程式碼中匯入的名稱應該符合 [設定 **屬性**  >  **一般**  >  **目標名稱**] 下專案屬性中的值。 

   在下列範例中， `"superfastcode"` 模組名稱表示您可以 `from superfastcode import fast_tanh` 在 Python 中使用，因為 `fast_tanh` 是在中定義 `superfastcode_methods` 。 C + + 專案內部的檔案名（例如 *module*）為不重要。

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. 新增 Python 在載入模組時呼叫的方法（必須命名 `PyInit_<module-name>` ），其中 *\<module-name>* 完全符合 c + + 專案的 **[一般**  >  **目標名稱**] 屬性。 也就是說，它會比對專案所建立之 *>.pyd* 檔的檔案名。

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. 重新建置 C++ 專案，以驗證您的程式碼。 如果您遇到錯誤，請參閱「 [疑難排解](#troubleshoot-compiling-failures) 」一節。

### <a name="use-pybind11"></a>使用 PyBind11

如果您已完成上一節中的步驟，您肯定注意到您使用了許多樣板程式碼，來建立 C++ 程式碼的必要模組結構。 PyBind11 可透過 c + + 標頭檔中的宏來簡化程式，以完成相同的結果，但程式碼較少。 

如需本節程式碼的詳細資訊，請參閱 [PyBind11 基本概念](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)。

1. 使用 pip 安裝 PyBind11： `pip install pybind11` 或 `py -m pip install pybind11` 。 

   或者，您可以使用 [Python 環境] 視窗安裝 PyBind11，然後在下一個步驟中使用其 [ **在 PowerShell 中開啟** ] 命令。

1. 在相同的終端機中，執行 `python -m pybind11 --includes` 或 `py -m pybind11 --includes` 。 

   這會列印您應該新增至專案 **C/c + +**  >  **[一般**  >  **其他 Include 目錄**] 屬性的路徑清單。 請務必移除前置詞 `-I` （如果有的話）。

1. 在全新 *module* 的最上方，不包含上一節所做的任何變更，包括 *pybind11 .h*：

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. 在 *module* 底部，使用 `PYBIND11_MODULE` 宏來定義 c + + 函式的進入點：

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

1. 建立 c + + 專案以驗證您的程式碼。 如果您遇到錯誤，請參閱下一節「針對編譯失敗進行疑難排解」，以取得解決方案。

### <a name="troubleshoot-compiling-failures"></a>針對編譯失敗進行疑難排解

C + + 模組可能因為下列原因而無法編譯：

- 錯誤：找不到 *Python .h* (**E1696：無法開啟來源檔案 "python. h"** 及/或 **C1083：無法開啟 include 檔： "Python. h"：沒有這種檔案或目錄**)  

  解決方案：確認專案屬性中的 [ **C/c + +**  >  **一般**  >  **其他 Include 目錄**] 中的路徑指向您的 Python 安裝的 [ *include* ] 資料夾。 請參閱[建立 Core C++ 專案](#create-the-core-c-projects)下的步驟 6。

- 錯誤：找不到 Python 程式庫 
 
   解決方案：確認專案屬性中 [**連結器**  >  **一般**  >  **其他程式庫目錄**] 中的路徑指向您的 Python 安裝的程式庫資料夾。 請參閱[建立 Core C++ 專案](#create-the-core-c-projects)下的步驟 6。

- 與目標架構相關的連結器錯誤
   
   解決方案：變更 c + + 目標的專案架構，使其符合您的 Python 安裝。 例如，如果您是以 c + + 專案為目標，但您的 Python 安裝是64位，請將 c + + 專案變更為 x64。

## <a name="test-the-code-and-compare-the-results"></a>測試程式碼，並比較結果

現在您已將 DLL 結構化成為 Python 延伸模組，您可以從 Python 專案參考它們、匯入模組，並使用其方法。

### <a name="make-the-dll-available-to-python"></a>讓 Python 使用 DLL

您可以使用數種方式將 DLL 提供給 Python。 以下是兩個要考慮的方法： 

* 如果 Python 專案和 c + + 專案位於相同的方案中，則第一個方法適用。 執行下列動作： 

   1. 在 **方案總管** 中，以滑鼠右鍵按一下 Python 專案中的 [ **參考** ] 節點，然後選取 [ **加入參考**]。 
   1. 在出現的對話方塊中，依序選取 [專案] 索引標籤、[superfastcode] 和 [superfastcode2] 專案，然後按一下 [確定]。

      ![顯示如何將參考新增至 "superfastcode" 專案的螢幕擷取畫面。](media/cpp-add-reference.png)

* 另一種方法是在您的 Python 環境中安裝模組，讓模組也可供其他 Python 專案使用。 如需詳細資訊，請參閱 [ **setuptools** 專案檔案](https://setuptools.readthedocs.io/)。 執行下列動作：

    1. 以滑鼠右鍵按一下 C++ 專案、建立名為 *setup.py* 的檔案，然後選取 [新增] > [新增項目]。 
    
    1. 選取 [ **c + + 檔案 ( .cpp)**，將檔案命名為 *setup.py*，然後選取 **[確定]**。
    
       將檔案命名為 *.py* 副檔名，會讓 Visual Studio 將它辨識為 Python 檔案（儘管使用 c + + 檔案範本）。 

       當檔案出現在編輯器中時，請適當地將下列程式碼貼入擴充方法：
    
        **針對 `CPython` (superfastcode 專案) 的延伸** 模組：
    
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
    
        **針對 `PyBind11` (superfastcode2 專案)**：
    
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
    
    1. 在 c + + 專案中建立名為 *pyproject* 的第二個檔案，並在其中貼上下列程式碼：
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. 若要建立延伸模組，請以滑鼠右鍵按一下 [開啟 *pyproject >gopkg.toml* ] 索引標籤，然後選取 [ **複製完整路徑**]。 使用之前，您將會從路徑刪除 *pyproject. >gopkg.toml* 名稱。
    
    1. 在 **方案總管** 中，以滑鼠右鍵按一下作用中的 python 環境，然後選取 [ **管理 python 套件**]。
    
        > [!Tip]
        > 如果您已經安裝封裝，您會看到它列在這裡。 繼續之前，請按一下 **X** 將其卸載。
    
    1. 在 [搜尋] 方塊中，貼上複製的路徑，從結尾刪除 *pyproject >gopkg.toml* ，然後選取 [輸入] 以從該目錄安裝模組。
    
        > [!Tip]
        > 如果因為許可權錯誤而導致安裝失敗，請將 *使用者* 新增至結尾，然後再次嘗試命令。


### <a name="call-the-dll-from-python"></a>從 Python 呼叫 DLL

依照上一節所述，將 DLL 提供給 Python 之後，您可以從 Python 程式碼呼叫和函式， `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` 並將其效能與 python 的執行進行比較。 若要呼叫 DLL，請執行下列動作：

1. 在您的 *.py* 檔案中新增下列幾行，以呼叫從 dll 匯出的方法，並顯示其輸出：

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. **選取 [不使用偵錯工具** 來啟動]，  >  或選取 Ctrl + F5，以執行 Python 程式。

    > [!NOTE]
    > 如果已停用 [ **啟動但不含調試** 程式] 命令，請在 **方案總管** 中，以滑鼠右鍵按一下 Python 專案，然後選取 [ **設定為啟始專案**]。  

    觀察 c + + 常式執行的速度比 Python 的執行速度大約五到20倍。 一般輸出會以下列形式呈現：

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. 您可以嘗試增加 `COUNT` 變數，讓差異更加明顯。 

    C + + 模組的 *調試* 程式執行速度也會比 *發行* 組建慢，因為 debug 組建較不優化，而且包含各種錯誤檢查。 您可以隨意切換這些設定以進行比較，但請記得回頭更新您稍早針對發行設定所設定的屬性。

在輸出中，您可能會看到 PyBind11 延伸模組的速度不如 CPython 延伸模組快，不過它應該比單純的 Python 執行速度快很多。 這項差異主要是因為您使用了 `METH_O` 不支援多個參數、參數名稱或關鍵字引數的呼叫。 PyBind11 會產生稍微複雜的程式碼，以提供更多類似 Python 的介面給呼叫者。 但是，由於測試程式碼會呼叫函數500000次，因此結果可能會大幅增強該額外負荷！

您可以藉由將 `for` 迴圈移至原生程式碼，來減少額外負荷。 這種方法會牽涉到使用[反覆運算器通訊協定](https://docs.python.org/c-api/iter.html) (或函式參數的 PyBind11 `py::iterable` 型別) 來處理每個元素。 [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args) 移除 Python 與 c + + 之間重複的轉換，是減少處理順序所需時間的有效方式。

### <a name="troubleshoot-importing-errors"></a>針對匯入錯誤進行疑難排解

如果您在 `ImportError` 嘗試匯入模組時收到訊息，您可以使用下列其中一種方式來解決此問題：

* 當您透過專案參考建立時，請確定您的 c + + 專案屬性符合為 Python 專案啟用的 Python 環境，特別是 *包含* 和連結 *庫* 目錄。

* 確定您的輸出檔案名稱為 *superfastcode. >.pyd*。 任何其他名稱或副檔名都會導致無法匯入。

* 如果您使用 *setup.py* 檔案來安裝模組，請檢查以確定您已在為 python 專案啟用的 python 環境中執行 *pip* 命令。 展開方案總管中的 Python 環境應該會顯示 *superfastcode* 的專案。

## <a name="debug-the-c-code"></a>偵錯 C++ 程式碼

Visual Studio 可支援同時偵錯 Python 和 C++ 程式碼。 在本節中，您會使用 *superfastcode* 專案來逐步完成程式。 *Superfastcode2* 專案的處理常式相同。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 Python 專案，選取 [**屬性**]，選取 [**調試** 程式] 索引標籤，然後選取 [ **debug**  >  **啟用機器碼調試** 程式] 選項。

    > [!Tip]
    > 當您啟用機器碼的偵錯工具時，Python 輸出視窗可能會在程式完成時立即關閉，而不會讓您正常 **按下任何鍵以繼續** 暫停。 
    >
    > 解決方案：若要在啟用機器碼偵錯工具之後強制暫停，請在 [偵錯工具] 索引標籤 `-i` 的 [**執行**  >  **解譯器引數**] 欄位中加入選項。 此引數會在程式碼執行之後，將 Python 解譯器置於互動模式中，此時它會等待您選取 Ctrl + Z，然後輸入以關閉視窗。 
    >
    > 或者，如果您不介意修改 Python 程式碼，您可以 `import os` `os.system("pause")` 在程式的結尾加入和語句。 此程式碼會複製原始的暫停提示。

1. 選取  >  [**儲存** 盤案] 以儲存屬性變更。

1. 在 [Visual Studio] 工具列上，將組建設定設為 **Debug**。

    ![Visual Studio 工具列上 [Debug] 設定的螢幕擷取畫面。](media/cpp-set-debug.png)

1. 由於程式碼通常會花較長的時間在偵錯工具中執行，因此您可能會想要將 `COUNT` *.py* 檔中的變數變更為比預設值小五倍的值。 例如，將它從 **500000** 變更為 **100000**。

1. 在您的 c + + 程式碼中，于方法的第一行設定中斷點 `tanh_impl` ，然後選取 **F5** 或 **Debug**  >  **開始調試** 程式來啟動偵錯工具。 

    呼叫中斷點程式碼時，偵錯工具就會停止。 如果未叫用中斷點，請檢查以確定設定已設定為 [ **Debug** ]，而且您已儲存專案（當您啟動偵錯工具時不會自動發生）。

    ![包含中斷點之 c + + 程式碼的螢幕擷取畫面。](media/cpp-debugging.png)

1. 在中斷點，您可以逐步執行 c + + 程式碼、檢查變數等等。 如需這些功能的詳細資訊，請參閱 [同時進行 Python 和 c + + 的調試](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)程式。

## <a name="alternative-approaches"></a>替代方法

您可以用各種方式建立 Python 延伸模組，如下表所述。 本文將討論前兩個數據列 `CPython` 和 `PyBind11` 。

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

您可以在 GitHub 的 [python （範例-vs-cpp-擴充](https://github.com/Microsoft/python-sample-vs-cpp-extension)功能）上找到此逐步解說中的完整範例。
