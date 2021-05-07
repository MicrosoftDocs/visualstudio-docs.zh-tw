---
title: Live Unit Testing
description: 瞭解如何在應用程式開發期間 Live Unit Testing，包括支援的架構以及如何設定 Live Unit Testing。
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: b9b78771c36dce26744ba74af63922cf1efa48e2
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798618"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>如何設定和使用 Live Unit Testing

當您在開發應用程式時，Live Unit Testing 會在背景自動執行任何受影響的單元測試，並即時呈現結果和程式碼涵蓋範圍。 當您修改程式碼時，Live Unit Testing 會針對您的變更如何影響現有測試，以及您所增加的新程式碼是否受到一或多個現有測試所涵蓋提供反饋。 當您進行錯誤修正或新增功能時，這會讓您以更好的方式提醒您撰寫單元測試。

> [!NOTE]
> Live Unit Testing 適用于以 .NET Core 為目標的 c # 和 Visual Basic 專案，或 Visual Studio 企業版中的 .NET Framework。

當您針對測試使用 Live Unit Testing 時，會保存您測試狀態的相關資料。 使用保存的資料可讓 Live Unit Testing 在回應程式碼變更時，動態地執行您的測試，以提供更優異的效能。

## <a name="supported-test-frameworks"></a>支援的測試架構

Live Unit Testing 適用於下表所列的三種熱門單元測試架構。 此外，也會顯示其介面卡和架構的最低支援版本。 單元測試架構全都可從 NuGet.org 取得。

|測試架構  |Visual Studio 配接器最小版本  |架構最小版本  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio 版本 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter 版本 3.5.1 |NUnit 版本 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

如果您的舊版 MSTest 測試專案參考 VisualStudio，而您不想要移至新版 MSTest NuGet 套件，請升級至 Visual Studio 2019 或 Visual Studio 2017。

在某些情況下，您可能需要明確還原專案所參考的 NuGet 套件，才能讓 Live Unit Testing 運作。 您可以執行這項作業，方法是執行方案的明確組建 (  >  從最上層 Visual Studio) 功能表選取 [組建 **重建方案**]，或在方案中還原套件 (以滑鼠右鍵按一下方案，然後選取 [**還原 NuGet 套件**]) 。

## <a name="configure"></a>設定

  >  從最上層 Visual Studio 功能表列中選取 [工具 **選項**]，然後在 [**選項**] 對話方塊的左窗格中選取 [ **Live Unit Testing** ]，以設定 Live Unit Testing。

> [!TIP]
> 啟用 Live Unit Testing 之後 (請參閱下一節、[啟動、暫停和停止 Live Unit Testing](#start-pause-and-stop)) ，也可以選取 [**測試** Live Unit Testing 選項] 來開啟 [**選項**] 對話方塊  >    >  ****。

下圖顯示對話方塊中可用的 Live Unit Testing 設定選項：

![Live Unit Testing 設定選項](./media/lut-options.png)

可設定的選項包括：

- 在解決方案完成建置及偵錯之後，Live Unit Testing 是否會暫停。

- 系統的電池電力低於指定的閾值時，Live Unit Testing 是否會暫停。

- Live Unit Testing 是否會在方案開啟時自動執行。

- 是否要啟用偵錯符號和 XML 文件註解的產生。

- 儲存保存資料的目錄。

- 能夠刪除所有保存資料的功能。 當 Live Unit Testing 以無法預期或非預期的方式運作時，這會很有用，這表示保存的資料已損毀。

- 測試案例超時的間隔。預設值為30秒。

- Live Unit Testing 建立的測試程序數目上限。

- Live Unit Testing 程序可以使用的記憶體數量上限。

- 寫入至 Live Unit Testing [輸出] 視窗的資訊層級。

   選項包括不記錄 ([無])、僅限錯誤訊息 ([錯誤])、錯誤與資訊訊息 ([資訊]，預設值) 或所有詳細資料 ([詳細資訊])。

   您也可以在 Live Unit Testing 的 [輸出] 視窗中顯示詳細資訊輸出，方法是將 "1" 的值指派給名為 `VS_UTE_DIAGNOSTICS` 的使用者層級環境變數，然後重新啟動 Visual Studio。

   若要在檔案中擷取來自 Live Unit Testing 的詳細 MSBuild 記錄訊息，請將 `LiveUnitTesting_BuildLog` 使用者層級環境變數設為該檔案的名稱，以包含記錄。

## <a name="start-pause-and-stop"></a>啟動、暫停和停止

若要啟用 Live Unit Testing，請選取 [**測試**]  >  **Live Unit Testing**  >  從最上層 Visual Studio 功能表 **開始**。 當 Live Unit Testing 啟用時，[ **Live Unit Testing** ] 功能表上的可用選項會從單一專案（ **開始**）變更為 [ **暫停** ] 和 [ **停止**]：

- **暫停** 會暫時暫停 Live Unit Testing。

  當 Live Unit Testing 暫停時，涵蓋範圍視覺效果不會出現在編輯器中，但會保留所有已收集的資料。 若要繼續進行 Live Unit Testing，請選取 [Live Unit Testing] 功能表中的 [繼續]。 Live Unit Testing 會執行必要的工作，以趕上暫停時所做的所有編輯，並適當地更新字元。

- **停止** 完全停止 Live Unit Testing。 Live Unit Testing 會捨棄所有已收集的資料。

> [!NOTE]
> 如果您在不包含單元測試專案的方案中啟動 Live Unit Testing，[ **暫停** ] 和 [ **停止** ] 選項會顯示在 [ **Live Unit Testing** ] 功能表上，但 Live Unit Testing 不會啟動。 [ **輸出** ] 視窗會顯示一則訊息，其開頭為「此解決方案不會參考支援的測試配接器 ...」。

您隨時都能暫時停止或完全停止 Live Unit Testing。 例如，您可能會想要這麼做，例如，如果您正在進行重構，並且知道您的測試將會中斷一段時間。

## <a name="view-coverage-visualization"></a>查看涵蓋範圍視覺效果

啟用之後，Live Unit Testing 會更新 Visual Studio 編輯器中的每一行程式碼，以顯示單元測試是否涵蓋您所撰寫的程式碼，以及涵蓋它的測試是否通過。 下圖顯示具有通過和失敗測試的程式程式碼，以及測試未涵蓋的程式程式碼。 僅由通過的測試所涵蓋的程式碼行會以綠色的 "✓" 裝飾，由一或多個失敗測試所涵蓋的程式碼行會以紅色的 "x" 裝飾，而沒有由任何測試所涵蓋的程式碼行則會以藍色的 "➖" 裝飾。

![Visual Studio 中的程式碼涵蓋範圍](./media/lut-codewindow.png)

當您在程式碼編輯器中修改程式碼時，就會立即更新 Live Unit Testing 涵蓋範圍視覺效果。 處理編輯時，視覺效果會變更，以指出資料不是最新狀態，方法是在通過、失敗及未涵蓋的符號下方新增圓形計時器影像，如下圖所示。

![使用計時器圖示 Visual Studio 中的程式碼涵蓋範圍](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>取得測試狀態的相關資訊

藉由將滑鼠暫留在程式碼視窗中的成功或失敗符號上方，您就能看到已針對該行做出多少測試。 若要查看個別測試的狀態，請選取符號：

![Visual Studio 中符號的測試狀態](./media/lut-failedinfo.png)

除了提供測試的名稱和結果之外，工具提示還可讓您重新執行或對測試集進行測試。 若選取工具提示中的一或多個測試，您也可以只執行那些測試或只針對那些測試進行偵錯。 這可讓您為您的測試進行偵錯，而不需要離開程式碼視窗。 進行偵錯時，除了觀察您已設定的任何中斷點之外，程式的執行也會在偵錯工具執行會傳回意外結果的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法時暫停。

當您將滑鼠暫留在工具提示中的失敗測試上方時，工具提示會展開以提供有關失敗的其他資訊，如以下影像所示。 若要直接流覽至失敗的測試，請在工具提示中按兩下它。

![Visual Studio 中的測試控管提示資訊失敗](./media/lut-failedmsg.png)

當您流覽至失敗的測試時，Live Unit Testing 會以視覺方式在方法簽章中指出具有下列各項的測試：

- 傳遞的 (會以半完整小燒杯表示，以及綠色的 "✓" ) 
- 無法 (半完整小燒杯以及紅色的 " 🞩 " ) 
- Live Unit Testing (半完整小燒杯以及藍色 "➖" ) 

非測試方法不會以任何符號裝飾。 下圖說明所有四種類型的方法。

![使用 pass 或 fail 符號 Visual Studio 中的測試方法](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>診斷並修正測試失敗

從失敗的測試中，您可以輕鬆地將產品程式碼進行測試、進行編輯，然後繼續開發您的應用程式。 由於 Live Unit Testing 會在背景執行，因此您不需要在 [debug]、[編輯] 和 [繼續] 迴圈期間停止並重新啟動 Live Unit Testing。

例如，上圖所示的測試失敗，是因測試方法中的非字母字元在 `true` 傳遞至方法時所傳回的錯誤假設所造成 <xref:System.Char.IsLower%2A?displayProperty=fullName> 。 更正測試方法之後，所有測試都應通過。 您不必暫停或停止 Live Unit Testing。

::: moniker range="vs-2017"
## <a name="test-explorer"></a>測試總管

**Test Explorer** 提供了一個介面，可讓您執行和偵測測試並分析測試結果。 Live Unit Testing 會與 [測試總管] 整合。 若未啟用或已停止 Live Unit Testing，[測試總管] 就會顯示上次執行測試時的單元測試狀態。 原始程式碼變更需要您重新執行測試。 相反地，啟用 Live Unit Testing 時，[測試總管] 中的單元測試狀態會立即更新。 您不需要明確地執行單元測試。

> [!TIP]
>    >    >  從最上層的 Visual Studio 功能表中選取 [測試 Windows **test Explorer** ]，以開啟 Live Unit Testing。

您可能會注意到，在 [ **測試瀏覽器** ] 視窗中，有些測試已淡出。例如，當您在開啟先前儲存的專案之後啟用 Live Unit Testing 時，[ **測試瀏覽器** ] 視窗會淡出所有失敗的測試，如下圖所示。 在此情況下，Live Unit Testing 已重新執行失敗的測試，但尚未重新執行成功的測試。 這是因為 Live Unit Testing 的持續性資料，表示自從上次成功執行測試之後，沒有任何變更。

![測試 Explorer 中的測試失敗](media/lut-test-explorer.png)

您可以從 [**測試瀏覽器**] 功能表選取 [**全部執行**] 或 [**執行**] 選項，以重新執行任何顯示為淡出的測試。 或者，在 [  **測試瀏覽器** ] 功能表中選取一個或多個測試，按一下滑鼠右鍵，然後從快顯功能表中選取 [ **執行選取的測試** ] 或 [偵測 **選取的測試** ]。 當測試執行時，它們會浮現在最上方。

在 Live Unit Testing 自動執行並更新測試結果，以及從 [測試總管] 明確執行測試之間，具有一些差異。 這些差異包括：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。
- Live Unit Testing 不會建立新的應用程式定義域來執行測試，而是從預設的定義域執行測試。 從 [測試總管] 視窗執行的測試會建立新的應用程式定義域。
- Live Unit Testing 會循序執行每個測試組件中的測試。 在 [ **測試瀏覽器** ] 視窗中，您可以選擇平行執行多個測試。
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing 視窗

**Live Unit Testing**（類似于 **Test Explorer**）提供了一個介面，可讓您執行和偵測測試並分析測試結果。 當 Live Unit Testing 啟用時，會立即更新 **Test Explorer** 中單元測試的狀態。 您不需要明確地執行單元測試。 當 Live Unit Testing 未啟用或已停止時， **Live Unit Testing** 會顯示上次執行測試時的單元測試狀態。 重新開機 Live Unit Testing 之後，需要變更原始程式碼，才能重新執行測試。

> [!TIP]
>   >    >  從最上層的 Visual Studio 功能表中選取 [測試 Live Unit Testing **開始**]，開始 Live Unit Testing。 您也可以使用 [  **View**  >  **Other Windows**  >  **Live Unit Testing] 視窗** 開啟 Live Unit Testing 視窗。

在 **Live Unit Testing** 視窗中，您可能會注意到有些測試淡出。例如，當您停止並重新啟動 Live Unit Testing 時， **Live Unit Testing** 視窗會淡化所有測試，如下圖所示。 淡出測試結果表示測試不是最新即時單元測試回合的一部分。 當偵測到測試變更或測試的相依性時，才會執行測試。 如果沒有任何變更，它會避免不必要地執行測試。 在此情況下，灰色的測試結果仍會處於「最新」狀態，不過它不是最新執行的一部分。

![在測試瀏覽器中淡出測試](media/vs-2019/lut-test-explorer.png)

您可以藉由進行程式碼變更，重新執行任何顯示為淡出的測試。

在 Live Unit Testing 自動執行並更新測試結果，以及從 [測試總管] 明確執行測試之間，具有一些差異。 這些差異包括：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。
- Live Unit Testing 不會建立新的應用程式定義域來執行測試，而是從預設的定義域執行測試。 從 [測試總管] 視窗執行的測試會建立新的應用程式定義域。
- Live Unit Testing 會循序執行每個測試組件中的測試。 在 [ **測試瀏覽器** ] 視窗中，您可以選擇平行執行多個測試。
::: moniker-end

## <a name="large-solutions"></a>大型解決方案

如果您的方案有10個以上的專案，Visual Studio 當您執行下列動作時，會顯示下列對話方塊：

- 開始 Live Unit Testing 且沒有任何保存的資料
- 選取 **工具**  >  **選項**  >  **Live Unit Testing**  >  **刪除保存的資料**

![針對大型專案的 Live Unit Testing 對話方塊](media/lut-large-project.png)

對話方塊會警告您，大型專案中大量測試的動態執行可能會嚴重影響效能。 如果您選取 [確定]，Live Unit Testing 會執行方案中的所有測試。 如果您選取 [取消]，便可以選取要執行的測試。 下一節將說明如何執行這項作業。

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>包含和排除測試專案與測試方法

針對有許多測試專案的方案，您可以控制專案中參與 Live Unit Testing 的專案和個別方法。 例如，如果您的方案具有數百個測試專案，則您可以選取一組目標測試專案來參與 Live Unit Testing。 有幾種方式可以完成這項作業，取決於您要排除專案或方案中的所有測試、包含或排除大部分的測試，還是排除個別測試。 Live Unit Testing 會將包含/排除狀態儲存為使用者設定，並在關閉並重新開啟方案時記住該狀態。

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>排除專案或方案中的所有測試

若要在單元測試中選取個別專案，請在啟動 Live Unit Testing 之後執行下列動作：

1. 以滑鼠右鍵按一下 **方案總管** 中的方案，然後選擇 [ **Live Unit Testing**  >  **排除**] 以排除整個方案。
1. 以滑鼠右鍵按一下您想要包含在測試中的每個測試專案，然後選擇 **Live Unit Testing**  >  **包含**]。

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>從程式碼編輯器視窗中排除個別測試

您可以使用程式碼編輯器視窗來包含或排除個別的測試方法。 在 [程式碼編輯器] 視窗中，以滑鼠右鍵按一下測試方法的簽章，然後選取下列其中一個選項：

- **Live Unit Testing**  > **包含 \<selected method>**
- **Live Unit Testing**  > **排除 \<selected method>**
- **Live Unit Testing**  > **排除全部 \<selected method>**

### <a name=&quot;exclude-tests-programmatically&quot;></a>以程式設計方式排除測試

您可以套用 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 屬性，來以程式設計方式排除方法、類別或結構，使它們不會在 Live Unit Testing 中報告它們的涵蓋範圍。

使用下列屬性來排除 Live Unit Testing 中的個別方法：

- 針對 xUnit：`[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- 針對 NUnit：`[Category("SkipWhenLiveUnitTesting")]`
- 針對 MSTest：`[TestCategory("SkipWhenLiveUnitTesting")]`

使用下列屬性，從 Live Unit Testing 中排除整個測試的元件：

- 針對 xUnit：`[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- 針對 NUnit：`[assembly: Category("SkipWhenLiveUnitTesting")]`
- 針對 MSTest：`[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>另請參閱

- [程式碼測試控管](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing 的 blog](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing 常見問題](live-unit-testing-faq.yml)
- [Channel 9 影片： Visual Studio 中的 Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
