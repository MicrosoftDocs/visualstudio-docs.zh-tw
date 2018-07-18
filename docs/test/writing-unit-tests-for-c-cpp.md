---
title: 在 Visual Studio 中撰寫 C/C++ 的單元測試
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: f0315027d6b0a3b57acc7b1651f0788d0b30bba1
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752075"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>在 Visual Studio 中撰寫 C/C++ 的單元測試

您可以使用**測試總管**視窗來撰寫及執行 C++ 單元測試，就像是其他語言一樣。 如需使用**測試總管**的詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

> [!NOTE]
> C++ 不支援 Live Unit Testing、自動程式化 UI 測試和 IntelliTest 等某些功能。

Visual Studio 隨附這些 C++ 測試架構，不需另外下載：

- 適用於 C++ 的 Microsoft 單元測試架構
- Google Test
- Boost.Test
- CTest

除了已安裝的架構之外，您也可以針對想要用於 Visual Studio 的任何架構撰寫自己的測試配接器。 測試配接器可以將單元測試與**測試總管**視窗整合。 [Visual Studio Marketplace](https://marketplace.visualstudio.com) 上提供幾個協力廠商配接器。 如需詳細資訊，請參閱[安裝協力廠商單元測試架構](install-third-party-unit-test-frameworks.md)。

**Visual Studio 2017 15.5 版**

- **Google Test 配接器**隨附作為 [使用 C++ 的桌面開發] 工作負載的預設元件。 它具有可透過**方案總管**中 [方案] 節點上的 [加入新的專案] 操作功能表新增至方案的專案範本，以及可透過 [工具] | [選項] 設定的選項。 如需詳細資訊，請參閱[如何：在 Visual Studio 中使用 Google Test](how-to-use-google-test-for-cpp.md)。

- **Boost.Test** 隨附作為 [使用 C++ 的桌面開發] 工作負載的預設元件。 它與**測試總管**整合但目前沒有專案範本，因此必須手動設定。 如需詳細資訊，請參閱[如何：在 Visual Studio 中使用 Boost.Test](how-to-use-boost-test-for-cpp.md)。

- **CTest** 支援隨附於 [使用 C++ 的桌面開發] 工作負載一部分的[適用於 Visual Studio 的 CMake 工具](/cpp/ide/cmake-tools-for-cpp)元件。 不過，CTest 尚未與**測試總管**完全整合。 如需詳細資訊，請參閱[如何：在 Visual Studio 中使用 CTest](how-to-use-ctest-for-cpp.md)。

**Visual Studio 2015 和更早版本**

您可以從 Visual Studio Marketplace 的[適用於 Boost.Test 的測試配接器](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest)和[適用於 Google Test 的測試配接器](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)下載 Boost.Test 配接器和 Google Test 配接器延伸模組。

## <a name="basic-test-workflow"></a>基本測試工作流程

下列各節說明協助您開始使用 C++ 單元測試的基本步驟。 Microsoft 和 Google Test 架構的基本組態非常類似。 Boost.Test 需要您手動建立測試專案。

### <a name="create-a-test-project"></a>建立測試專案

您會在一或多個測試專案中定義及執行測試，且這些專案與您要測試的程式碼位於相同的方案中。 若要將新的測試專案新增至現有的方案，請在**方案總管**中，以滑鼠右鍵按一下方案節點，並選擇 [新增] | [新增專案]。 然後在左窗格中選擇 [Visual C++] 和 [測試]，並從中間窗格選擇其中一個專案類型。 下圖顯示安裝 [使用 C++ 的桌面開發] 工作負載時可用的測試專案：

![C++ 測試專案](media/cpp-new-test-project.png)

### <a name="create-references-to-other-projects-in-the-solution"></a>在方案中建立其他專案的參考

若要讓您的測試程式碼存取要測試之專案中的函式，請在測試專案中新增專案的參考。 在**方案總管**中，以滑鼠右鍵按一下測試專案節點，並選擇 [新增] | [參考]。 然後在對話方塊中選擇您要測試的專案。

![加入參考](media/cpp-add-ref-test-project.png)

### <a name="add-include-directives-for-header-files"></a>針對標頭檔新增 #include 指示詞

接下來，在單元測試的 .cpp 檔中，針對宣告您要測試之類型和函式的任何標頭檔，新增一個 `#include` 指示詞。 鍵入 `#include "`，IntelliSense 即會啟用以協助您選擇。 針對任何其他標頭重複步驟。

![新增 include 指示詞](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>撰寫測試方法

> [!NOTE]
> 本節說明適用於 C/C++ 的 Microsoft 單元測試架構語法。 相關文件如下：[Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 參考](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)。 如需 Google Test 文件，請參閱 [Google Test 入門](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md)。 如需 Boost.Test，請參閱 [Boost Test Library: The Unit Test Framework](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Boost Test 程式庫：單元測試架構)。

測試專案中的 .cpp 檔為您定義虛設常式類別和方法，以示範如何撰寫測試程式碼。 請注意，這些簽章使用 TEST_CLASS 和 TEST_METHOD 巨集，因此可從測試總管視窗探索方法。

![新增 include 指示詞](media/cpp-write-test-methods.png)

TEST_CLASS 和 TEST_METHOD 是 [Microsoft 原生測試架構](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)的一部分。 **測試總管**以類似的方式來探索其他支援架構中的測試方法。

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

您可以將「特徵」新增至測試方法，來指定測試擁有者、優先順序和其他資訊。 接著可以使用這些值來排序及分組**測試總管**中的測試。 如需詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

### <a name="run-the-tests"></a>執行測試

1. 在 [測試] 功能表上，選擇 [Windows] > [測試總管]。 下圖顯示其測試尚未執行的測試專案。

   ![執行測試前的 [測試總管]](media/cpp-test-explorer.png)

   > [!NOTE]
   > 目前無法將 CTest 與**測試總管**整合。 從 CMake 主功能表執行 CTest 測試。

1. 如果視窗中未顯示您所有的測試，請建置測試專案，方法是在**方案總管**中，以滑鼠右鍵按一下其節點，然後選擇 [建置] 或 [重建]。

1. 在測試總管中，選擇 [全部執行]，或選取您要執行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。 執行所有測試之後，視窗會顯示哪些測試成功及哪些測試失敗：

![執行測試後的 [測試總管]](media/cpp-test-explorer-passed.png)

針對失敗的測試，此訊息會提供詳細資料以協助診斷原因。 您可以用滑鼠右鍵按一下失敗的測試，然後選擇 [偵錯選取的測試] 以逐步執行發生失敗的函式。

如需使用**測試總管**的詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

如需與單元測試相關的最佳做法，請參閱[單元測試基本概念](unit-test-basics.md)

## <a name="see-also"></a>另請參閱

[對程式碼進行單元測試](unit-test-your-code.md)
