---
title: 撰寫 C/C++ 的單元測試
description: 使用各種測試框架(包括 CTest、Boost.Test 和 Google 測試)在 Visual Studio 中編寫C++單元測試。
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 0eaf41dc0bf3e21dfbf4018261844181d594f0d5
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649606"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>在 Visual Studio 中撰寫 C/C++ 的單元測試

您可以使用**測試資源管理器**視窗編寫並運行C++單元測試。 它的工作原理與其他語言一樣。 如需使用**測試總管**的詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

> [!NOTE]
> C++ 不支援 Live Unit Testing、自動程式化 UI 測試和 IntelliTest 等某些功能。

Visual Studio 隨附這些 C++ 測試架構，不需另外下載：

- 適用於 C++ 的 Microsoft 單元測試架構
- Google Test
- Boost.Test
- CTest

除了使用已安裝的框架外,您還可以為在 Visual Studio 中使用的任何框架編寫自己的測試適配器。 測試配接器可以將單元測試與**測試總管**視窗整合。 [Visual Studio Marketplace](https://marketplace.visualstudio.com) 上提供幾個協力廠商配接器。 有關詳細資訊,請參閱[安裝第三方單元測試框架](install-third-party-unit-test-frameworks.md)。

**Visual Studio 2017 和更新版本 (Professional 與 Enterprise)**

C++ 單元測試專案支援 [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)。

**Visual Studio 2017 及更新版本 (所有版本)**

- **Google 測試配接器**包含在**具有C++工作負載的桌面開發**預設元件中。 它有一個項目範本,您可以添加到解決方案。 使用**解決方案資源管理員**中解決方案節點上的「**添加新專案**」右鍵單擊功能表來添加它。 它您可以使用**工具** > **選項設定的選項**。 有關詳細資訊,請參閱[:在視覺工作室中使用 Google 測試](how-to-use-google-test-for-cpp.md)。

- **Boost.Test**是桌面開發預設元件,**具有C++** 工作負載。 它與**測試資源管理器**集成,但當前沒有專案範本。 必須手動配置它。 有關詳細資訊,請參閱[:在可視化工作室中使用 Boost.Test](how-to-use-boost-test-for-cpp.md)。

- **CTest** 支援已隨附於 [使用 C++ 的桌面開發]**** 工作負載之一部分的 [C++ CMake 工具]**** 元件。 有關詳細資訊,請參閱[:在可視化工作室中使用 CTest。](how-to-use-ctest-for-cpp.md)

**Visual Studio 2015 和更早版本**

您可以在可視化工作室應用商店下載 Google 測試適配器和擴增器.測試適配器擴展。 測試[與測試卡](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest)機的[Google 測試](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)。

## <a name="basic-test-workflow"></a>基本測試工作流程

下列各節說明協助您開始使用 C++ 單元測試的基本步驟。 對於微軟和谷歌測試框架,基本配置是相似的。 Boost.Test 需要您手動建立測試專案。

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立測試專案

在一個或多個測試專案中定義和運行測試。 在要測試的代碼相同的解決方案中創建專案。 要向現有解決方案添加新測試專案,請右鍵單擊**解決方案資源管理器**中的"解決方案"節點。 在彈出式功能表中,選擇 **「添加新** > **專案**」。。 將 [語言]**** 設為 C++，然後在搜尋方塊中鍵入 "test"。 下圖顯示安裝 [使用 C++ 進行桌面開發]**** 及 [UWP 開發]**** 工作負載後，可使用的測試專案：

![Visual Studio 2019 中的 C++ 測試專案](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立測試專案

在一個或多個測試專案中定義和運行測試。 在要測試的代碼相同的解決方案中創建專案。 要新增新的測試專案,請右鍵單擊**解決方案資源管理器**中的「解決方案」節點,然後選擇「**添加新** > **專案**」。 在左側窗格中,選擇 **「可視C++測試**」。。 然後,從中心窗格中選擇一個項目類型。 下圖顯示安裝 [使用 C++ 的桌面開發]**** 工作負載時可用的測試專案：

![C++ 測試專案](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>在方案中建立其他專案的參考

要啟用對受測專案中的函數的訪問,請添加對測試專案中專案的引用。 右鍵單擊**解決方案資源管理器**中的測試專案節點,查看彈出式功能表。 選擇 **「添加** > **參考**」。 在"添加參考"對話框中,選擇要測試的專案。

![新增參考](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>連結至物件或程式庫檔案

若測試程式碼沒有匯出您要測試的函式，您可以將輸出 .obj 或 .lib 檔案新增至測試專案的相依性。 有關詳細資訊,請參閱[將測試連結到物件或函式庫檔](how-to-use-microsoft-test-framework-for-cpp.md#object_files)。

### <a name="add-include-directives-for-header-files"></a>針對標頭檔新增 #include 指示詞

接下來，在單元測試的 *.cpp* 檔中，針對宣告您要測試之類型和函式的任何標頭檔，新增一個 `#include` 指示詞。 鍵入 `#include "`，IntelliSense 即會啟用以協助您選擇。 針對任何其他標頭重複步驟。

![新增 include 指示詞](media/cpp-add-includes-test-project.png)

為了避免必須在源檔中的每個包含語句中鍵入完整路徑,可以在**專案** > **屬性** > **C/C++** > **常規** > **附加包含目錄中**添加所需的資料夾。

### <a name="write-test-methods"></a>撰寫測試方法

> [!NOTE]
> 本節說明適用於 C/C++ 的 Microsoft 單元測試架構語法。 相關文件如下：[Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 參考](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)。 如需 Google Test 文件，請參閱 [Google Test primer](https://github.com/google/googletest/blob/master/googletest/docs/primer.md) (Google Test 入門)。 如需 Boost.Test，請參閱 [Boost Test library: The unit test framework](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Boost Test 程式庫：單元測試架構)。

測試專案中的 *.cpp*檔具有為您定義的存根類別和方法。 它們顯示了如何編寫測試代碼的範例。 簽名使用TEST_CLASS和TEST_METHOD宏,這使得這些方法可以從**測試資源管理器**視窗中發現。

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

您可以將*特徵*添加到測試方法以指定測試擁有者、優先順序和其他資訊。 接著可以使用這些值來排序及分組**測試總管**中的測試。 如需詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

### <a name="run-the-tests"></a>執行測試

1. 在 [測試]**** 功能表上，選擇 [Windows]**** > [測試總管]****。 下圖顯示其測試尚未執行的測試專案。

   ![執行測試前的測試資源管理員](media/cpp-test-explorer.png)

   > [!NOTE]
   > 目前無法將 CTest 與**測試總管**整合。 從 CMake 主功能表執行 CTest 測試。

1. 如果並非所有測試在視窗中可見,請透過右鍵單擊**解決方案資源管理器**中的節點並選擇**生成**或**重建**來生成測試專案。

1. 測試**資源管理員中**,選擇 **「全部執行**」或選擇要執行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。 執行所有測試之後，視窗會顯示哪些測試成功及哪些測試失敗：

![執行測試後的 [測試總管]](media/cpp-test-explorer-passed.png)

針對失敗的測試，此訊息會提供詳細資料以協助診斷原因。 右鍵單擊彈出功能表的失敗測試。 選擇 **「調試所選測試**」以單步執行發生故障的函數。

如需使用**測試總管**的詳細資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

有關單元測試的詳細資訊,請參閱[單元測試基礎知識](unit-test-basics.md)

## <a name="use-codelens"></a>使用 CodeLens

**Visual Studio 2017 和更新版本 (Professional 與 Enterprise 版)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)允許您在不離開代碼編輯器的情況下快速查看單元測試的狀態。

您可以採用下列任何一種方式為 C++ 單元測試專案初始化 CodeLens：

- 編輯及建置測試專案或方案。
- 重建您的專案或方案。
- 從**測試資源管理員**視窗運行測試。

初始化后,您可以在每個單元測試上方看到測試狀態圖示。

![C++ CodeLens 圖示](media/cpp-test-codelens-icons.png)

按一下圖示以取得詳細資訊，或執行單元測試或對單元測試進行偵錯：

![C++ CodeLens 執行及偵錯](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>另請參閱

- [單元測試代碼](unit-test-your-code.md)
