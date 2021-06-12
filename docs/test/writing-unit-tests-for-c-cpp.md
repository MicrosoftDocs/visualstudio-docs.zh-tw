---
title: 撰寫 C/C++ 的單元測試
description: 使用各種測試架構（包括 CTest、提升、測試和 Google Test），在 Visual Studio 中撰寫 c + + 單元測試。
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 877c9163d05f458ce45a46d6b3e6d14e354df591
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042883"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>在 Visual Studio 中撰寫 C/C++ 的單元測試

您可以使用 [ **測試瀏覽器** ] 視窗撰寫和執行 c + + 單元測試。 它的運作方式與其他語言一樣。 如需使用 **測試總管** 的詳細資訊，請參閱 [使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

> [!NOTE]
> C++ 不支援 Live Unit Testing、自動程式化 UI 測試和 IntelliTest 等某些功能。

Visual Studio 隨附這些 C++ 測試架構，不需另外下載：

- 適用於 C++ 的 Microsoft 單元測試架構
- Google Test
- Boost.Test
- CTest

除了使用已安裝的架構之外，您還可以針對您想要在 Visual Studio 中使用的任何架構，撰寫自己的測試介面卡。 測試配接器可以將單元測試與 **測試總管** 視窗整合。 [Visual Studio Marketplace](https://marketplace.visualstudio.com) 上提供幾個協力廠商配接器。 如需詳細資訊，請參閱 [安裝協力廠商單元測試](install-third-party-unit-test-frameworks.md)架構。

**Visual Studio 2017 和更新版本 (Professional 與 Enterprise)**

C++ 單元測試專案支援 [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)。

**Visual Studio 2017 及更新版本 (所有版本)**

- **Google Test 介面卡** 隨附為 **使用 c + +** 工作負載的桌面開發預設元件。 它有一個可新增至方案的專案範本。 使用 **方案總管** 中方案節點上的 [**加入新的專案**] 右鍵功能表，將它加入。 它也有可透過 [工具]   >  **選項** 設定的選項。 如需詳細資訊，請參閱 [如何：使用 Visual Studio 中的 Google Test](how-to-use-google-test-for-cpp.md)。

- **提升。測試** 是以 **c + +** 工作負載的桌面開發預設元件的形式包含。 它與 **Test Explorer** 整合，但目前沒有專案範本。 必須手動設定。 如需詳細資訊，請參閱[如何：在 Visual Studio 中使用 [提升]。](how-to-use-boost-test-for-cpp.md)

- **CTest** 支援已隨附於 [使用 C++ 的桌面開發] 工作負載之一部分的 [C++ CMake 工具] 元件。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中使用 CTest](how-to-use-ctest-for-cpp.md)。

**Visual Studio 2015 和更早版本**

您可以下載 Google Test 介面卡，並提升 Visual Studio Marketplace 的測試介面卡擴充功能。 在測試介面卡上找到它們， [以提升。測試](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) 和 [測試介面卡以進行 Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)。

## <a name="basic-test-workflow"></a>基本測試工作流程

下列各節說明協助您開始使用 C++ 單元測試的基本步驟。 Microsoft 和 Google Test framework 的基本設定都很類似。 Boost.Test 需要您手動建立測試專案。

::: moniker range=">=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立測試專案

您可以在一或多個測試專案中定義及執行測試。 您可以在與您想要測試的程式碼相同的方案中建立專案。 若要將新的測試專案加入至現有的方案，請在 **方案總管** 中的方案節點上按一下滑鼠右鍵。 在快顯功能表中，選擇 [**加入**  >  **新專案**]。 將 [語言] 設為 C++，然後在搜尋方塊中鍵入 "test"。 下圖顯示安裝 [使用 C++ 進行桌面開發] 及 [UWP 開發] 工作負載後，可使用的測試專案：

![Visual Studio 2019 中的 C++ 測試專案](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立測試專案

您可以在一或多個測試專案中定義及執行測試。 您可以在與您想要測試的程式碼相同的方案中建立專案。 若要加入新的測試專案，請在 **方案總管** 中的方案節點上按一下滑鼠右鍵，然後選擇 [**加入**  >  **新專案**]。 在左窗格中，選擇 [ **Visual C++ 測試**]。 然後，從中央窗格中選擇其中一個專案類型。 下圖顯示安裝 [使用 C++ 的桌面開發] 工作負載時可用的測試專案：

![C++ 測試專案](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>在方案中建立其他專案的參考

若要啟用受測試專案中之函式的存取權，請在測試專案中加入專案的參考。 以滑鼠右鍵按一下 **方案總管** 中的 [測試專案] 節點，以取得快顯功能表。 選擇 [**加入**  >  **參考**]。 在 [加入參考] 對話方塊中，選擇您要測試) 的專案 (。

![新增參考](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>連結至物件或程式庫檔案

若測試程式碼沒有匯出您要測試的函式，您可以將輸出 .obj 或 .lib 檔案新增至測試專案的相依性。 如需詳細資訊，請參閱 [將測試連結至物件或程式庫](how-to-use-microsoft-test-framework-for-cpp.md#object_files)檔案。

### <a name="add-include-directives-for-header-files"></a>針對標頭檔新增 #include 指示詞

接下來，在單元測試的 *.cpp* 檔中，針對宣告您要測試之類型和函式的任何標頭檔，新增一個 `#include` 指示詞。 鍵入 `#include "`，IntelliSense 即會啟用以協助您選擇。 針對任何其他標頭重複步驟。

![方案總管的螢幕擷取畫面，其中顯示以 IntelliSense 醒目提示要包含的標頭檔來加入的 #include 指示詞。](media/cpp-add-includes-test-project.png)

若要避免在來源檔案的每個 include 語句中輸入完整路徑，您可以在 **專案**  >  **屬性**  >  **C/c + +**  >  **一般**  >  **其他 include 目錄** 中新增必要的資料夾。

### <a name="write-test-methods"></a>撰寫測試方法

> [!NOTE]
> 本節說明適用於 C/C++ 的 Microsoft 單元測試架構語法。 相關文件如下：[Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 參考](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)。 如需 Google Test 文件，請參閱 [Google Test primer](https://github.com/google/googletest/blob/master/docs/primer.md) (Google Test 入門)。 如需 Boost.Test，請參閱 [Boost Test library: The unit test framework](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Boost Test 程式庫：單元測試架構)。

您測試專案中的 *.cpp* 檔案有為您定義的存根類別和方法。 這些範例顯示如何撰寫測試程式碼的範例。 簽章會使用 TEST_CLASS 並 TEST_METHOD 宏，讓您可以從 [ **測試瀏覽器** ] 視窗中找到這些方法。

![[測試瀏覽器] 視窗的螢幕擷取畫面，其中顯示 unittest1 .cpp 程式碼檔案，其中包含使用 TEST_CLASS 和 TEST_METHOD 宏的存根類別和方法。](media/cpp-write-test-methods.png)

TEST_CLASS 和 TEST_METHOD 是 [Microsoft 原生測試架構](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)的一部分。 **測試總管** 以類似的方式來探索其他支援架構中的測試方法。

TEST_METHOD 傳回 void。 若要產生測試結果，請使用 `Assert` 類別中的靜態方法，根據預期結果來測試實際結果。 在下列範例中，假設 `MyClass` 具有接受 `std::string` 的建構函式。 我們可以測試此建構函式是否會如預期般初始化類別：

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

在上述範例中，`Assert::AreEqual` 呼叫的結果會判斷測試成功或失敗。 Assert 類別包含用於比較預期與實際結果的許多其他方法。

您可以將 *特性* 新增至測試方法，以指定測試擁有者、優先順序和其他資訊。 接著可以使用這些值來排序及分組 **測試總管** 中的測試。 如需詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

### <a name="run-the-tests"></a>執行測試

1. 在 [測試] 功能表上，選擇 [Windows] > [測試總管]。 下圖顯示其測試尚未執行的測試專案。

   ![執行測試之前的 Test Explorer](media/cpp-test-explorer.png)

   > [!NOTE]
   > 目前無法將 CTest 與 **測試總管** 整合。 從 CMake 主功能表執行 CTest 測試。

1. 如果未在視窗中顯示所有測試，請在 **方案總管** 中以滑鼠右鍵按一下其節點，然後選擇 [ **建立** ] 或 [ **重建**]，以建立測試專案。

1. 在 [ **測試瀏覽器**] 中，選擇 [ **全部執行**]，或選取您想要執行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。 執行所有測試之後，視窗會顯示哪些測試成功及哪些測試失敗：

![執行測試後的 [測試總管]](media/cpp-test-explorer-passed.png)

針對失敗的測試，此訊息會提供詳細資料以協助診斷原因。 以滑鼠右鍵按一下快顯功能表的 [失敗的測試]。 選擇 [偵測 **選取的測試** ]，逐步執行發生失敗的函式。

如需使用 **測試總管** 的詳細資訊，請參閱 [使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

如需單元測試的相關詳細資訊，請參閱 [單元測試基本概念](unit-test-basics.md)

## <a name="use-codelens"></a>使用 CodeLens

**Visual Studio 2017 和更新版本 (Professional 與 Enterprise 版)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) 可讓您快速查看單元測試的狀態，而不需要離開程式碼編輯器。

您可以採用下列任何一種方式為 C++ 單元測試專案初始化 CodeLens：

- 編輯及建置測試專案或方案。
- 重建您的專案或方案。
- 從 [ **測試瀏覽器** ] 視窗執行測試。

初始化之後，您可以在每個單元測試上方看到測試狀態圖示。

![C++ CodeLens 圖示](media/cpp-test-codelens-icons.png)

按一下圖示以取得詳細資訊，或執行單元測試或對單元測試進行偵錯：

![C++ CodeLens 執行及偵錯](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](unit-test-your-code.md)
