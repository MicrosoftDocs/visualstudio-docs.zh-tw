---
title: Live Unit Testing
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 34200e8719ef25de3c54c612b967cf3d4f9bab85
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223695"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>如何設定及使用即時儲存測試

在開發應用程式時,Live 單元測試會在後台自動運行任何受影響的單元測試,並實時顯示結果和代碼覆蓋率。 當您修改程式碼時，Live Unit Testing 會針對您的變更如何影響現有測試，以及您所增加的新程式碼是否受到一或多個現有測試所涵蓋提供反饋。 這輕輕地提醒您編寫單元測試,因為您正在進行錯誤修復或添加新功能。

> [!NOTE]
> 即時單元測試可用於 Visual Studio 企業版中針對 .NET Core 或 .NET 框架的 C# 和可視化基本專案。

當您對測試使用即時單元測試時,它會保留有關測試狀態的數據。 使用持久數據允許即時單元測試在動態運行測試以回應代碼更改時提供卓越的性能。

## <a name="supported-test-frameworks"></a>支援的測試架構

Live Unit Testing 適用於下表所列的三種熱門單元測試架構。 還顯示了其適配器和框架的最低支援版本。 單元測試架構全都可從 NuGet.org 取得。

|測試架構  |Visual Studio 配接器最小版本  |架構最小版本  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio 版本 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter 版本 3.5.1 |NUnit 版本 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

如果您有較舊的基於 MSTest 的測試專案,引用 Microsoft.VisualStudio.QualityTools.UnitTestFramework,並且不希望遷移到較新的 MSTest NuGet 包,則升級到 Visual Studio 2019 或 Visual Studio 2017。

在某些情況下,您可能需要顯式還原專案引用的 NuGet 包,以使即時單元測試正常工作。 可以通過執行解決方案的顯式生成(從頂級可視化工作室功能表中選擇**生成** > **重建解決方案**)或還原解決方案中的包(右鍵單擊解決方案並選擇 **"還原 NuGet 包**")來執行此操作。

## <a name="configure"></a>設定

以從頂級 Visual Studio 選單列選擇 **「工具** > **選項**」,然後在 **「選項」** 對話框的左邊窗格選擇 **「即時儲存測試」來設定即時儲存入測試**。

> [!TIP]
> 啟用即時單元測試後(請參閱下一節"[開始"、"暫停"和"停止即時單元測試](#start-pause-and-stop)"),還可以通過選擇 **「測試** > **即時單元測試** > **選項**」打開 **「選項**」對話方塊。

下圖顯示了對話框中可用的即時儲存單元測試設定選項:

![即時儲存配置選項](./media/lut-options.png)

可設定的選項包括：

- 在解決方案完成建置及偵錯之後，Live Unit Testing 是否會暫停。

- 系統的電池電力低於指定的閾值時，Live Unit Testing 是否會暫停。

- Live Unit Testing 是否會在方案開啟時自動執行。

- 是否要啟用偵錯符號和 XML 文件註解的產生。

- 儲存保存資料的目錄。

- 能夠刪除所有保存資料的功能。 當即時單元測試以不可預測或意外的方式進行時,這非常有用,這表明持久化數據已損壞。

- 測試用例超時的時間間隔。默認值為 30 秒。

- Live Unit Testing 建立的測試程序數目上限。

- Live Unit Testing 程序可以使用的記憶體數量上限。

- 寫入至 Live Unit Testing [輸出]**** 視窗的資訊層級。

   選項包括不記錄 ([無]****)、僅限錯誤訊息 ([錯誤]****)、錯誤與資訊訊息 ([資訊]****，預設值) 或所有詳細資料 ([詳細資訊]****)。

   您也可以在 Live Unit Testing 的 [輸出]**** 視窗中顯示詳細資訊輸出，方法是將 "1" 的值指派給名為 `VS_UTE_DIAGNOSTICS` 的使用者層級環境變數，然後重新啟動 Visual Studio。

   若要在檔案中擷取來自 Live Unit Testing 的詳細 MSBuild 記錄訊息，請將 `LiveUnitTesting_BuildLog` 使用者層級環境變數設為該檔案的名稱，以包含記錄。

## <a name="start-pause-and-stop"></a>啟動、暫停與停止

要啟用即時單元測試,請從頂級可視化工作室功能表中選擇 **「測試** > **即時單元測試** > **開始**」。。 開啟即時單元測試後,「**即時單元測試」** 選單上可用的選項將從單個項目 **「開始」** 變更為 **「暫停****」 與「停止**」

- **暫停**暫時暫停即時單元測試。

  暫停即時單元測試時,覆蓋率可視化不會顯示在編輯器中,但收集的所有數據都將保留。 若要繼續進行 Live Unit Testing，請選取 [Live Unit Testing] 功能表中的 [繼續]****。 即時單元測試執行必要的工作,以趕上在暫停時進行的所有編輯,並適當地更新字形。

- **停止**完全停止即時單元測試。 Live Unit Testing 會捨棄所有已收集的資料。

> [!NOTE]
> 如果在不包含單元測試專案的解決方案中啟動即時單元測試,則 **「暫停**」和 **「停止」** 選項將顯示在 **「即時單元測試」** 功能表上,但即時單元測試不會啟動。 **輸出**視窗顯示一條消息,開頭是"此解決方案未引用任何受支持的測試適配器..."。

您隨時都能暫時停止或完全停止 Live Unit Testing。 例如,如果您正處於重構中,並且知道測試將中斷一段時間,則可能需要執行此操作。

## <a name="view-coverage-visualization"></a>檢視範圍視覺化

啟用後,即時單元測試將更新 Visual Studio 編輯器中的每一行代碼,以顯示您編寫的代碼是否包含在單元測試中,以及覆蓋它的測試是否通過。 下圖顯示了具有通過測試和失敗的測試的代碼行,以及測試未涵蓋的代碼行。 僅由通過的測試所涵蓋的程式碼行會以綠色的 "✓" 裝飾，由一或多個失敗測試所涵蓋的程式碼行會以紅色的 "x" 裝飾，而沒有由任何測試所涵蓋的程式碼行則會以藍色的 "➖" 裝飾。

![視覺化工作室中的程式碼覆蓋率](./media/lut-codewindow.png)

當您修改代碼編輯器中的代碼時,即時單元測試覆蓋率可視化會立即更新。 在處理編輯時,可視化效果會通過添加經過、失效且未覆蓋的符號下方的圓形計時器圖像來指示數據不是最新的,如下圖所示。

![帶計時器圖示的視覺化工作室中的代碼覆蓋率](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>取得測試狀態的資訊

藉由將滑鼠暫留在程式碼視窗中的成功或失敗符號上方，您就能看到已針對該行做出多少測試。 要檢視測試測試的狀態,請選擇符號:

![視覺化工作室中符號的測試狀態](./media/lut-failedinfo.png)

除了提供測試的名稱和結果外,工具提示還允許您重新運行或調試測試集。 若選取工具提示中的一或多個測試，您也可以只執行那些測試或只針對那些測試進行偵錯。 這可讓您為您的測試進行偵錯，而不需要離開程式碼視窗。 進行偵錯時，除了觀察您已設定的任何中斷點之外，程式的執行也會在偵錯工具執行會傳回意外結果的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法時暫停。

當您將滑鼠暫留在工具提示中的失敗測試上方時，工具提示會展開以提供有關失敗的其他資訊，如以下影像所示。 要直接導航到失敗的測試,請在工具提示中按兩下它。

![視覺工作室中失敗的測試工具提示資訊](./media/lut-failedmsg.png)

導覽到失敗的測試時,即時單元測試在方法簽名中直觀地指示具有以下功能的測試:

- 通過(由半滿的燒杯以及綠色"*"表示)
- 失敗(半滿燒杯連同紅色"")🞩
- 不參與現場單元測試(半滿燒杯和藍色"➖")

非測試方法不會以任何符號裝飾。 下圖說明瞭所有四種類型的方法。

![視覺工作室中具有通過或失敗符號的測試方法](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>診斷並修正測試失敗

通過失敗的測試,您可以輕鬆地調試產品代碼、進行編輯並繼續開發應用程式。 由於即時單元測試在後台運行,因此在調試、編輯和繼續循環期間無需停止並重新啟動即時單元測試。

例如,上一張圖像中顯示的測試失敗是由於測試方法中的錯誤假設,即非字母字元在傳遞給`true`<xref:System.Char.IsLower%2A?displayProperty=fullName>該方法時返回。 更正測試方法后,所有測試都應通過。 您不必暫停或停止即時單元測試。

::: moniker range="vs-2017"
## <a name="test-explorer"></a>測試總管

**測試資源管理員**提供了一個介面,允許您運行和調試測試並分析測試結果。 Live Unit Testing 會與 [測試總管]**** 整合。 若未啟用或已停止 Live Unit Testing，[測試總管]**** 就會顯示上次執行測試時的單元測試狀態。 原始程式碼變更需要您重新執行測試。 相反地，啟用 Live Unit Testing 時，[測試總管]**** 中的單元測試狀態會立即更新。 您無需顯式運行單元測試。

> [!TIP]
> 從頂級視覺化工作室選單**中選擇測試** > **Windows** > **測試資源管理員**來開啟**即時單元測試**。

您可能會在 **「測試資源管理器」** 視窗中注意到某些測試已淡出。例如,在打開以前保存的專案後啟用即時單元測試時,**測試資源管理器**視窗已淡出所有測試,但失敗測試,如下圖所示。 在這種情況下,即時單元測試已重新運行失敗的測試,但它沒有重新運行成功的測試。 這是因為即時單元測試的持久數據表明自上次成功運行測試以來沒有任何更改。

![測試資源管理員中的測試失敗](media/lut-test-explorer.png)

您可以通過從 **「測試資源管理器**」功能表中選擇 **「全部執行**」或 **「運行」** 選項來重新執行出現褪色的任何測試。 或者,在 **「測試資源管理器」** 選單中選擇一個或多個測試,右鍵單擊,然後從彈出功能表中選擇 **「運行選定測試**」或 **「調試所選測試**」。 當測試執行時，它們會浮現在最上方。

在 Live Unit Testing 自動執行並更新測試結果，以及從 [測試總管]**** 明確執行測試之間，具有一些差異。 這些差異包括：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。
- Live Unit Testing 不會建立新的應用程式定義域來執行測試，而是從預設的定義域執行測試。 從 [測試總管]**** 視窗執行的測試會建立新的應用程式定義域。
- Live Unit Testing 會循序執行每個測試組件中的測試。 在**測試資源管理員視窗**中,您可以選擇並行執行多個測試。
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>即時儲存測試視窗

**即時單元測試**(類似於**測試資源管理員**)提供了一個介面,允許您運行和調試測試並分析測試結果。 啟用即時單元測試後,**測試資源管理員**中的單元測試的狀態將立即更新。 您無需顯式運行單元測試。 當即時單元測試未啟用或停止時,**即時單元測試**會在上次測試運行時顯示單元測試的狀態。 重新啟動即時單元測試後,需要更改原始程式碼才能重新運行測試。

> [!TIP]
> 通過從頂級可視化工作室功能表中選擇 **「測試** > **即時單元測試** > **開始」** 啟動即時單元測試。 您還可以使用 **「查看** > **其他 Windows** > **即時單元測試視窗**」打開**即時單元測試**視窗。

您可能會在**即時單元測試**視窗中注意到某些測試已淡出。例如,當您停止並重新啟動即時單元測試時,「**即時單元測試」** 視窗將淡出所有測試,如下圖所示。 已淡出測試結果表明,該測試不是最新實時單元測試運行的一部分。 僅當檢測到對測試或測試的依賴項的更改時,測試才會運行。 如果沒有更改,則避免不必要地運行測試。 在這種情況下,灰顯的測試結果仍然是"最新的",儘管它不是最近運行的一部分。

![在測試資源管理員中淡出測試](media/vs-2019/lut-test-explorer.png)

您可以通過更改代碼來重新執行出現褪色的任何測試。

在 Live Unit Testing 自動執行並更新測試結果，以及從 [測試總管]**** 明確執行測試之間，具有一些差異。 這些差異包括：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。
- Live Unit Testing 不會建立新的應用程式定義域來執行測試，而是從預設的定義域執行測試。 從 [測試總管]**** 視窗執行的測試會建立新的應用程式定義域。
- Live Unit Testing 會循序執行每個測試組件中的測試。 在**測試資源管理員視窗**中,您可以選擇並行執行多個測試。
::: moniker-end

## <a name="large-solutions"></a>大型解決方案

如果解決方案有 10 個或更多專案,則可視化工作室會在以下操作時顯示以下對話方塊:

- 啟動即時單元測試,沒有持久資料
- 選擇**工具** > **選項** > **即時儲存入選中** > **移除持久資料**

![針對大型專案的 Live Unit Testing 對話方塊](media/lut-large-project.png)

該對話框警告您,在大型專案中動態執行大量測試可能會嚴重影響性能。 如果您選取 [確定]****，Live Unit Testing 會執行方案中的所有測試。 如果您選取 [取消]****，便可以選取要執行的測試。 以下部分將介紹如何執行此操作。

## <a name="include-and-exclude-test-projects-and-test-methods"></a>包含和排除測試專案與測試方法

對於具有許多測試項目的解決方案,您可以控制專案中哪些專案和單個方法參與即時單元測試。 例如，如果您的方案具有數百個測試專案，則您可以選取一組目標測試專案來參與 Live Unit Testing。 有許多方法可以做到這一點,具體取決於是要排除專案或解決方案中的所有測試、包括或排除大多數測試,還是排除單個測試。 Live Unit Testing 會將包含/排除狀態儲存為使用者設定，並在關閉並重新開啟方案時記住該狀態。

### <a name="exclude-all-tests-in-a-project-or-solution"></a>排除項目或解決方案中的所有測試

若要在單元測試中選取個別專案，請在啟動 Live Unit Testing 之後執行下列動作：

1. 以滑鼠右鍵按一下 [方案總管]**** 中的方案，然後依序選擇 [即時測試]**** > [排除]**** 來排除整個方案。
1. 右鍵按下您希望包含在測試中的每個測試項目,然後選擇 **「即時測試** > **包括**」。。

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>從程式碼編輯器視窗排除單測試

您可以使用程式碼編輯器視窗來包含或排除個別的測試方法。 右鍵按一下代碼編輯器視窗中的測試方法的簽名,然後選擇以下選項之一:

- **即時測試** > **\<包括 選取方法>**
- **即時測試** > **\<排除 所選方法>**
- **即時測試** > **排除所有\<但 選擇的方法>**

### <a name="exclude-tests-programmatically"></a>以程式設計方式排除測試

您可以套用 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 屬性，來以程式設計方式排除方法、類別或結構，使它們不會在 Live Unit Testing 中報告它們的涵蓋範圍。

使用以下屬性從即時單元測試中排除單方法:

- 針對 xUnit：`[Trait("Category", "SkipWhenLiveUnitTesting")]`
- 針對 NUnit：`[Category("SkipWhenLiveUnitTesting")]`
- 針對 MSTest：`[TestCategory("SkipWhenLiveUnitTesting")]`

使用以下屬性從即時儲存測試中排除整個測試程式集:

- 針對 xUnit：`[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- 針對 NUnit：`[assembly: Category("SkipWhenLiveUnitTesting")]`
- 針對 MSTest：`[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>另請參閱

- [程式碼測試工具](https://visualstudio.microsoft.com/vs/testing-tools/)
- [即時單元測試部落格](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [即時單元測試常見問題解答](live-unit-testing-faq.md)
- [頻道 9 視頻:可視化工作室的即時單元測試](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
