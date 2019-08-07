---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2cbde88ee12118f9f59271f897e81ec18c24eb4e
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68662055"
---
# <a name="live-unit-testing-with-visual-studio"></a>Visual Studio 的 Live Unit Testing

當您開發應用程式時，Live Unit Testing 會在背景自動執行任何受影響的單元測試，並立即在 Visual Studio IDE 中呈現即時的結果和程式碼涵蓋範圍。 當您修改程式碼時，Live Unit Testing 會針對您的變更如何影響現有測試，以及您所增加的新程式碼是否受到一或多個現有測試所涵蓋提供反饋。 這可在您進行錯誤修正或新增功能時，委婉地提醒您撰寫單元測試。

> [!NOTE]
> Live Unit Testing 適用於以 Visual Studio Enterprise Edition 中 .NET Core 或 .NET Framework 為目標的 C# 和 Visual Basic 專案。

當您使用 Live Unit Testing 進行測試時，Live Unit Testing 會保存有關測試狀態的資料。 它使用保存資料的能力可讓 Live Unit Testing 提供卓越的效能，同時隨著程式碼變更動態執行您的測試。

## <a name="supported-test-frameworks"></a>支援的測試架構
Live Unit Testing 適用於下表所列的三種熱門單元測試架構。 其配接器與架構所支援的最小版本也列於表格中。 單元測試架構全都可從 NuGet.org 取得。

|測試架構  |Visual Studio 配接器最小版本  |架構最小版本  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio 版本 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter 版本 3.5.1 |NUnit 版本 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

如果您的舊版 MSTest 測試專案參考 `Microsoft.VisualStudio.QualityTools.UnitTestFramework`，但您不想要移至新版 MSTest NuGet 套件，請升級至 Visual Studio 2017 15.4 版或更新版本。

在某些情況下，您可能需要明確地還原方案中的專案所參考的 NuGet 封裝，才能使 Live Unit Testing 運作。 若要執行此動作，您可以在啟用 Live Unit Testing 之前，明確地建置方案 (從最上層的 Visual Studio 功能表中依序選取 [建置]   > [重建方案]  )，或是在方案中還原套件 (以滑鼠右鍵按一下方案，然後選取 [還原 NuGet 套件]  )。

## <a name="configure-live-unit-testing"></a>設定 Live Unit Testing

您可以設定 Live Unit Testing，方法是從最上層的 Visual Studio 功能表列中依序選取 [工具]   > [選項]  ，然後在 [選項]  對話方塊的左窗格中選取 [Live Unit Testing]  。

> [!TIP]
> 只要啟用了 Live Unit Testing (請參閱下一節[啟動、暫停和停止 Live Unit Testing](#start-pause-and-stop-live-unit-testing))，您就也可以選取 [測試]   > [Live Unit Testing]   > [選項]  以開啟 [選項]  對話方塊。

下圖顯示對話方塊中提供的 Live Unit Testing 組態選項：

  ![Image](./media/lut-options.png)

可設定的選項包括：

- 在解決方案完成建置及偵錯之後，Live Unit Testing 是否會暫停。

- 系統的電池電力低於指定的閾值時，Live Unit Testing 是否會暫停。

- Live Unit Testing 是否會在方案開啟時自動執行。

- 是否要啟用偵錯符號和 XML 文件註解的產生。

- 儲存保存資料的目錄。

- 能夠刪除所有保存資料的功能。 當 Live Unit Testing 發生無法預測或未預期的行為時，保存資料可能損毀，因此此功能很實用。

- 測試案例逾時的時間間隔；預設值為 30 秒。

- Live Unit Testing 建立的測試程序數目上限。

- Live Unit Testing 程序可以使用的記憶體數量上限。

- 寫入至 Live Unit Testing [輸出]  視窗的資訊層級。

   選項包括不記錄 ([無]  )、僅限錯誤訊息 ([錯誤]  )、錯誤與資訊訊息 ([資訊]  ，預設值) 或所有詳細資料 ([詳細資訊]  )。

   您也可以在 Live Unit Testing 的 [輸出]  視窗中顯示詳細資訊輸出，方法是將 "1" 的值指派給名為 `VS_UTE_DIAGNOSTICS` 的使用者層級環境變數，然後重新啟動 Visual Studio。

   若要在檔案中擷取來自 Live Unit Testing 的詳細 MSBuild 記錄訊息，請將 `LiveUnitTesting_BuildLog` 使用者層級環境變數設為該檔案的名稱，以包含記錄。

## <a name="start-pause-and-stop-live-unit-testing"></a>啟動、暫停和停止 Live Unit Testing

您可以從最上層的 Visual Studio 功能表依序選取 [測試]   > [Live Unit Testing]   > [啟動]  ，來啟用 Live Unit Testing。 啟用 Live Unit Testing 時，[Live Unit Testing]  功能表上的可用選項會從單一項目 ([啟動]  ) 變更為 [暫停]  、[停止]  與 [重新啟動]  。

> [!NOTE]
> 如果您在未包含單元測試專案的方案中啟動 Live Unit Testing，則 [暫停]  、[停止]  和 [Reset Clean] (全新重設)  選項會出現在 [Live Unit Testing]  功能表上，但不會啟動 Live Unit Testing。 [輸出]  視窗會顯示開頭如下的訊息：「此方案未參考支援的測試配接器...」

您隨時都能暫時停止或完全停止 Live Unit Testing。 例如，如果您正在進行重構，並知道測試會因此中斷一段時間，則您可能會想要執行此動作。 這三個功能表選項如下：

- **暫停**：它會暫時停止 Live Unit Testing。

    當 Live Unit Testing 暫停時，您涵蓋範圍的視覺效果不會出現在編輯器中，但會保留所有已收集的資料。 若要繼續進行 Live Unit Testing，請選取 [Live Unit Testing] 功能表中的 [繼續]  。 Live Unit Testing 會執行必要的工作來更新在暫停期間所做的所有編輯，並會適當地更新字符。

- **停止**：可完全停止 Live Unit Testing。 Live Unit Testing 會捨棄所有已收集的資料。

- **重設清除**，這會停止 Live Unit Testing、刪除保存資料，並重新啟動 Live Unit Testing。

- **選項**，這會開啟[設定 Live Unit Testing](#configure-live-unit-testing) 一節所述的 [選項]  對話方塊。

## <a name="view-coverage-visualization-in-the-editor-as-you-type"></a>在鍵入期間於編輯器中檢視涵蓋範圍的視覺效果

一旦啟用之後，Live Unit Testing 就會更新 Visual Studio 編輯器中的每個程式碼行，以顯示單元測試是否會涵蓋您撰寫的程式碼，以及涵蓋該程式碼的測試是否順利通過。  下圖顯示顯示具有通過及失敗測試的程式碼行，以及不受測試涵蓋的程式碼行。 僅由通過的測試所涵蓋的程式碼行會以綠色的 "✓" 裝飾，由一或多個失敗測試所涵蓋的程式碼行會以紅色的 "x" 裝飾，而沒有由任何測試所涵蓋的程式碼行則會以藍色的 "➖" 裝飾。

  ![Image](./media/lut-codewindow.png)

當您在程式碼編輯器中修改程式碼時，系統會立即更新 Live Unit Testing 涵蓋範圍的視覺效果。 處理編輯時，視覺效果會變更來表示資料不是最新狀態，並會在通過、失敗及未涵蓋符號下方新增圓形計時器圖案，如下圖所示。

  ![Image](./media/lut-codeupdating.png)

## <a name="get-information-on-successful-or-failed-tests"></a>取得成功或失敗測試的相關資訊

藉由將滑鼠暫留在程式碼視窗中的成功或失敗符號上方，您就能看到已針對該行做出多少測試。 如果您按一下該符號，就能看見個別測試的狀態，如下圖所示：

  ![Image](./media/lut-failedinfo.png)

除了提供測試名稱與測試結果之外，工具提示也可以讓您重新執行測試集合，以及使用偵錯工具執行測試集合。 若選取工具提示中的一或多個測試，您也可以只執行那些測試或只針對那些測試進行偵錯。 這可讓您為您的測試進行偵錯，而不需要離開程式碼視窗。 進行偵錯時，除了觀察您已設定的任何中斷點之外，程式的執行也會在偵錯工具執行會傳回意外結果的 [`Assert`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert) 方法時暫停。

當您將滑鼠暫留在工具提示中的失敗測試上方時，工具提示會展開以提供有關失敗的其他資訊，如以下影像所示。 如果您按兩下工具提示中的失敗測試，就能直接瀏覽至該測試。

  ![Image](./media/lut-failedmsg.png)

當您巡覽至失敗測試時，Live Unit Testing 也會以視覺方式在方法簽章中指出已通過的測試 (以一個半滿燒杯與綠色 "✓" 表示)、失敗的測試 (以一個半滿燒杯與紅色 "🞩" 表示)，或未參與 Live Unit Testing 的測試 (以一個半滿燒杯與藍色 "➖" 表示)。 非測試方法不會以任何符號裝飾。 下圖說明全部四種類型的方法。

  ![Image](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>診斷並修正測試失敗

從失敗的測試，您可以輕鬆地針對產品程式碼進行偵錯、做出編輯，並繼續開發應用程式。 由於 Live Unit Testing 是在背景執行，因此您不需要在偵錯、編輯和繼續的循環期間停止並重新啟動 Live Unit Testing。

例如，上圖所示的測試失敗，是因測試方法中錯誤假設非字母字元在傳遞到 <xref:System.Char.IsLower%2A?displayProperty=fullName> 方法時，會傳回 `true` 而導致。 當我們更正測試方法之後，就發現所有測試均會通過。 當我們執行此動作時，不需暫停或停止 Live Unit Testing。

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing 和測試總管

一般而言，[測試總管]  會提供介面，讓您能夠針對測試結果進行執行、偵錯及分析。 Live Unit Testing 會與 [測試總管]  整合。 若未啟用或已停止 Live Unit Testing，[測試總管]  就會顯示上次執行測試時的單元測試狀態。 原始程式碼變更需要您重新執行測試。 相反地，啟用 Live Unit Testing 時，[測試總管]  中的單元測試狀態會立即更新。 您不再需要明確地執行單元測試。

> [!NOTE]
> 您可以依序選取最上層 Visual Studio 功能表中的 [測試]   > [視窗]   > [測試總管]  來開啟 [測試總管]  。

您可能會發現 [測試總管]  視窗中的某些測試呈現淡出效果。例如，當您在開啟先前儲存的專案之後啟用 Live Unit Testing 時，[測試總管]  視窗以淡出效果顯示失敗之測試以外的所有測試，如下圖所示。 在此案例中，Live Unit Testing 已重新執行失敗的測試，但尚未重新執行成功的測試，因為 Live Unit Testing 的保存資料指出上次測試成功執行之後，資料並未變更。

  ![Image](media/lut-test-explorer.png)

您可以從 [測試總管]  功能表選取 [全部執行]  或 [執行]  選項；或選取 [測試總管]  功能表中的一或多個測試並按一下滑鼠右鍵，然後從快顯功能表選取 [執行選取的測試]  或 [偵錯選取的測試]  ，以重新執行任何以淡出效果顯示的測試。 當測試執行時，它們會浮現在最上方。

在 Live Unit Testing 自動執行並更新測試結果，以及從 [測試總管]  明確執行測試之間，具有一些差異。 這些差異包括：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。
- Live Unit Testing 不會建立新的應用程式定義域來執行測試，而是從預設的定義域執行測試。 從 [測試總管]  視窗執行的測試會建立新的應用程式定義域。
- Live Unit Testing 會循序執行每個測試組件中的測試。 您可以在 [測試總管]  視窗中，選擇並行執行多項測試的選項。

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing 與大型方案

如果您的方案具有 10 個或更多的專案，當啟動 Live Unit Testing 而其中並沒有保留資料，或從最上層 Visual Studio 功能表選取 [測試]   > [Live Unit Testing]   > [重設清除]  選項時，Visual Studio 會顯示下列對話方塊，以警告在大型專案中動態執行大量測試可能會嚴重影響效能。 如果您選取 [確定]  ，Live Unit Testing 會執行方案中的所有測試。 如果您選取 [取消]  ，便可以選取要執行的測試。 如需執行這項操作的資訊，請參閱下面的[包含和排除測試專案與測試方法](#include-and-exclude-test-projects-and-test-methods)一節。

 ![針對大型專案的 Live Unit Testing 對話方塊](media/lut-large-project.png)

## <a name="include-and-exclude-test-projects-and-test-methods"></a>包含和排除測試專案與測試方法

針對具有許多測試專案的方案，您可以控制要讓哪些專案，以及專案中的哪些個別方法參與 Live Unit Testing。 例如，如果您的方案具有數百個測試專案，則您可以選取一組目標測試專案來參與 Live Unit Testing。 有數種方式可以這樣做，這取決於您要在專案或方案中排除所有測試、您要包含或排除大部分的測試，或您是否要個別排除測試。 Live Unit Testing 會將包含/排除狀態儲存為使用者設定，並在關閉並重新開啟方案時記住該狀態。

**排除專案或方案中的所有測試**

若要在單元測試中選取個別專案，請在啟動 Live Unit Testing 之後執行下列動作：

1. 以滑鼠右鍵按一下 [方案總管]  中的方案，然後依序選擇 [即時測試]   > [排除]  來排除整個方案。
1. 以滑鼠右鍵按一下您想要包含於測試中的每個測試專案，然後依序選擇 [即時測試]   > [包含]  。

**從程式碼編輯器視窗排除個別測試**

您可以使用程式碼編輯器視窗來包含或排除個別的測試方法。 以滑鼠右鍵按一下程式碼編輯器視窗中測試方法的簽章，然後選取 [即時測試]   > [包含 [選取的方法]]  、[即時測試]   > [排除 [選取的方法]]  或 [即時測試]   > [全部排除 [選取的方法除外]]  ，其中「選取的方法」是您在程式碼視窗中選取之方法的名稱。

**以程式設計方式排除測試**

您可以套用 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 屬性，來以程式設計方式排除方法、類別或結構，使它們不會在 Live Unit Testing 中報告它們的涵蓋範圍。

您也可以使用下列屬性將個別方法從 Live Unit Testing 排除：

- 針對 xUnit：`[Trait("Category", "SkipWhenLiveUnitTesting")]`
- 針對 NUnit：`[Category("SkipWhenLiveUnitTesting")]`
- 針對 MSTest：`[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>另請參閱

- [程式碼測試工具](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing 部落格](https://go.microsoft.com/fwlink/?linkid=842514) \(英文\)
- [即時單元測試常見問題集](live-unit-testing-faq.md)
- [Channel 9 影片：Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105) (Visual Studio 中的 Live Unit Testing)
