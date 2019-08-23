---
title: 測試清單編輯器常見問題集
ms.date: 08/14/2019
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: jillfra
ms.openlocfilehash: a37cdea4206dafe657dc8cf8adbbcf98ce18afc9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551855"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio 測試總管常見問題集
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Visual Studio 2019 中依據特性群組的位置為何？
這個特性群組已移至資料行。 有了 Visual Studio 2019 16.2 版中多個且可自訂的階層，我們認為將特性納入為群組產生了不必要的視覺複雜度。 我們一定會聽取對這項設計的意見反映！ https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

現在您可以用滑鼠右鍵按一下 [測試總管] 中的資料行，然後選取 [資料行]。 檢查 [特性] 資料行，它會出現在 [測試總管] 中。 您現在可以依據您感興趣的特性來篩選此資料行。

![顯示特性資料行](media/vs-2019/trait-column.png)
![篩選特性資料行](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>動態測試探索

**[測試總管] 找不到動態定義的測試。(例如理論、自訂配接器、自訂特徵、#ifdef 等項目)我如何探索這些測試？**

::: moniker range=">=vs-2019"
建置專案來執行以組件為基礎的探索。
::: moniker-end
::: moniker range="vs-2017"
建置專案並確保已在 [工具]  > [選項]  > [測試]  中開啟以組件為基礎的探索。
::: moniker-end
[即時測試探索](https://go.microsoft.com/fwlink/?linkid=862824)是來源型的測試探索。 其無法探索使用理論、自訂配接器、自訂特徵及 `#ifdef` 陳述式等項目的測試，因為這些項目均已在執行階段中定義。 需要組建才能準確找到這些測試。 在 Visual Studio 2017 15.6 版及更新版本中，以組件為基礎的探索 (傳統型探索) 只會在建置之後執行。 這項設定表示當您在編輯時，即時測試探索會盡可能找到更多測試，而組件型探索允許動態定義的測試在組建之後顯示。 即時測試探索會改善回應性，但仍然可讓您在建置後取得完整且精確的結果。

## <a name="test-explorer--plus-symbol"></a>測試總管 '+' (加號) 符號

**顯示在測試總管最上面一行的 '+' (加號) 符號代表什麼？**

'+' (加號) 表示可以在執行以組件為基礎的探索時，在建置後探索更多測試。 如果在專案中偵測到動態定義的測試，就會出現此符號。

![加號摘要行](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>以組件為基礎的探索

**我的專案已經無法使用以組件為基礎的探索。如何再將它開啟？**

前往 [工具]  > [選項]  > [測試]  ，然後選取 [在建置後從建置後的組件探索其他測試]  。

![以組件為基礎的選項](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>即時測試探索

**現在當我打字時，測試會顯示在測試總管中，而不需要建置我的專案。哪些方面已變更？**

此功能稱為[即時測試探索](https://go.microsoft.com/fwlink/?linkid=862824)。 這項功能使用 Roslyn 分析器來探索測試並即時填入 [測試總管]，因此不需要建置您的專案。 如需動態定義測試 (例如理論或自訂特徵) 的測試探索行為詳細資訊，請參閱[動態測試探索](#dynamic-test-discovery)。

## <a name="real-time-test-discovery-compatibility"></a>即時測試探索相容性

**哪些程式設計語言和測試架構可以使用「即時測試探索」？**

[即時測試探索](https://go.microsoft.com/fwlink/?linkid=862824)以 Roslyn 編譯器建置，因此只適用於受控語言 (C# 和 Visual Basic)。 目前，即時測試探索只適用於 xUnit、NUnit 和 MSTest 架構。

## <a name="test-explorer-logs"></a>測試總管記錄

**如何開啟測試總管的記錄？**

巡覽至 [工具]   > [選項]   > [測試]  並於該處尋找 [記錄] 區段。

## <a name="uwp-test-discovery"></a>UWP 測試探索

**為什麼我在部署應用程式前無法探索到 UWP 專案中的測試？**

部署應用程式時，UWP 測試會以其他執行階段為目標。 這表示若要精確找到 UWP 專案的測試，您不僅需要建置專案，還需要進行部署。

## <a name="test-explorer-sorting"></a>測試總管排序

**階層架構檢視中的排序測試結果是如何運作的？**

階層架構檢視會依字母順序排序排序結果，而不根據輸出。 其他分組依據設定通常會依序按照輸出及字母順序來排序測試結果。 查看下圖中顯示各類分組依據選項以供比較。 您可在[此 GitHub 問題中](https://github.com/Microsoft/vstest/issues/1425)對設計提出意見反應。

![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>測試總管階層檢視

**在階層檢視中，父節點群組旁邊會有通過、失敗、略過和未執行的圖示。這些圖示代表什麼意思？**

專案、命名空間和類別群組旁的圖示，會顯示出該群組內的測試狀態。 請參閱下表。

![測試總管階層圖示](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>依檔案路徑搜尋

**在 [測試總管] 搜尋方塊中，已無「檔案路徑」篩選條件。**

Visual Studio 2017 15.7 版已移除 [測試總管]  搜尋方塊中的檔案路徑篩選條件。 此功能的使用率很低，且排除這項功能可讓 [測試總管] 更快速地擷取測試方法。 如果此變更中斷您的開發流程，請在[開發人員社群](https://developercommunity.visualstudio.com/)提交意見反應來告訴我們。

## <a name="remove-undocumented-interfaces"></a>移除未記載的介面

**某些與測試相關的 API 不再存在於 Visual Studio 2019。哪些方面已變更？**

在 Visual Studio 2019 中，會移除一些先前標記為公用，但從未正式記載的測試視窗 API。 它們在 Visual Studio 2017 中標示為「已淘汰」，可為延伸模組維護人員提供初期警告。 據我們所知，很少有延伸模組發現及依存於這些 API。 這些包括 `IGroupByProvider`、`IGroupByProvider<T>`、`KeyComparer`、`ISearchFilter`、`ISearchFilterToken`、`ISearchToken` 和 `SearchFilterTokenType`。 如果這項變更會影響您的延伸模組，請在 [Developer Community](https://developercommunity.visualstudio.com) (開發人員社群) 提出 Bug 讓我們知道。

::: moniker range="vs-2017"
## <a name="test-adapter-nuget-reference"></a>測試配接器 NuGet 參考

**在 Visual Studio 2017 15.8 版中， 已探索到我的註冊，但不會執行。**

所有測試專案的 csproj 檔案中都必須包含 .NET 測試配接器 NuGet 參考。 如果未包含在其中，若測試配接器延伸模組的探索在建置之後開始，或使用者嘗試執行選取的測試，專案上就會顯示下列測試輸出：

**測試專案t {} 未參考任何 .NET NuGet 配接器。這個專案的測試探索或執行會無法執行。建議您在解決方案中的每個 .NET 測試專案參考 NuGet 測試配接器。**

專案必須使用測試配接器 NuGet 套件，而非使用測試配接器延伸模組。 使用持續整合時，此需求可大幅改善效能並減少問題的發生。 在[版本資訊](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension)深入了解 .NET 測試配接器延伸模組淘汰。

> [!NOTE]
> 如果您使用 NUnit 2 Test Adapter 且無法移轉至 NUnit 3 Test Adapter，您可以關閉這個新的探索行為，位置是 Visual Studio 15.8 版的 [工具]   > [選項]   > [測試]  。

![工具選項中的 [測試總管] 配接器行為](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>找不到 UWP TestContainer

**我無法在 Visual Studio 2017 15.7 版及更新版本中執行 UWP 測試。**

最近的 UWP 測試專案指定一個測試平台建置屬性，可讓識別測試應用程式時的效能更佳。 如果您有在 Visual Studio 15.7 版之前初始化的 UWP 測試專案，您可能會在 [輸出]   > [測試]  中看到此錯誤：

**System.AggregateException:One or more errors occurred. ---> System.InvalidOperationException:The following TestContainer was not found {} at Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync>d__61.MoveNext()**

修正這個錯誤：

- 使用下列程式碼來更新您的測試專案組建屬性：

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- 使用下列程式碼來更新 TestPlatform SDK 版本：

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>使用功能旗標

**如何開啟功能旗標以試用新的測試功能？**

功能旗標是用來將產品的實驗性或未完成的部分，遞送給想在功能正式推出前提供意見反應的熱衷使用者。 它們可能會造成 IDE 體驗不穩定。 建議您僅在處於虛擬環境等安全開發環境時使用這些項目。 功能旗標一律是「自行承擔使用風險」的設定。 您可以使用 [Feature Flags 延伸模組](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)，或透過開發人員命令提示字元來開啟實驗性功能。

![Feature Flag 延伸模組](media/testex-featureflag.png)

若要透過 Visual Studio 開發人員命令提示字元來開啟功能旗標，請使用以下命令。 變更 Visual Studio 在機器上的安裝路徑，並變更您希望使用的功能旗標登錄機碼。

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> 您可以使用相同的命令來關閉旗標，方法是在 dword 之後使用 0 作為值而不是 1。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) (針對現有的程式碼建立和執行單元測試)
- [對程式碼進行單元測試](unit-test-your-code.md)
- [Live Unit Testing 常見問題集](live-unit-testing-faq.md)
