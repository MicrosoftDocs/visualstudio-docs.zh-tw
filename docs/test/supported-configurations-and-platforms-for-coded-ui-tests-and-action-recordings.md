---
title: 自動程式化 UI 測試的組態和平台
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e18e50537f35080f9796f4a090b3806953ae5170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75845815"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>自動程式碼 UI 測試和動作記錄的支援組態和平台

Visual Studio 企業版的自動程式碼 UI 測試的支援組態與平台會列在下表中。 這些組態也套用至使用 [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]建立的動作記錄。

> [!NOTE]
> 自動程式碼 UI 測試處理序的權限必須和待測 App 的權限相同。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**需求**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>支援的設定

| 組態 | 支援 |
|-| - |
| 作業系統 | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| 32 位元/ 64 位元支援 | 執行 32 位元 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 的 32 位元 Windows 可以測試 32 位元應用程式。<br /><br /> 執行 32 位元 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 的 64 位元 Windows，可以測試具有「UI 同步處理」的 32 位元 WOW 應用程式。<br /><br /> 執行 32 位元 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 的 64 位元 Windows 可以測試沒有「UI 同步處理」的 64 位元 Windows Form 和 WPF 應用程式。 |
| 架構 | x86 和 x64 **注意事項：** 除非在 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本執行，否則 64 位元模式不支援 Internet Explorer。 |
| .NET | .NET 2.0、3.0、3.5、4 和 4.5。 **注意：**  [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 和 Visual Studio 都需要 .NET 4 才能運作。 然而，支援使用列出的 .NET 版本開發的應用程式。 |

> [!NOTE]
> 「*UI 同步處理* 」(UI Synchronization) 功能可在每個控制項的訊息佇列中驗證播放。 如果控制項沒有回應傳送至它的事件，則會重新傳送事件。

## <a name="platform-support"></a>平台支援

| 平台 | 支援層級 |
|-| - |
| Windows Phone App | 只支援 WinRT-XAML 架構的 Phone 應用程式。 |
| UWP 應用程式 | 只支援以 XAML 為基礎 UWP 的應用程式。 |
| 通用 Windows App | 只支援手機和桌上型電腦上以 XAML 為基礎的通用 Windows App。 |
| Edge | 不支援錄製動作步驟或使用產生器來檢視物件屬性。 測試可以在邊緣瀏覽器上播放，使用 Visual Studio 2015 更新 2 和更高版本通過使用[編碼 UI 交叉瀏覽器測試擴展](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)。 |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **重要事項︰** 只有在桌上型電腦才支援 Internet Explorer 10。 <br /><br /> Internet Explorer 11 **重要事項︰** 只有在桌上型電腦才支援 Internet Explorer 11。 | 完全支援。<br /><br /> -   **在 Internet 資源管理器 9 和 Internet 資源管理器 10 中支援 HTML5：** 編碼的 UI 測試支援 HTML5 控制項的記錄、播放和驗證：音訊、視頻、進度列和滑塊。 有關詳細資訊，請參閱[在編碼的 UI 測試中使用 HTML5 控制項](../test/using-html5-controls-in-coded-ui-tests.md)。 **警告：**      如果您在 Internet Explorer 10 中建立自動程式化 UI 測試，可能無法使用 Internet Explorer 9 或 Internet Explorer 8 執行。 這是因為 Internet Explorer 10 包含 HTML5 控制項，例如 Audio、Video、ProgressBar 和 Slider。 Internet Explorer 9 或 Internet Explorer 8 無法辨識這些 HTML5 控制項。 同樣地，使用 Internet Explorer 9 的自動程式碼 UI 測試可能包含一些 Internet Explorer 8 無法辨識的 HTML5 控制項。<br />-   **支援 Internet 資源管理器 10 拼寫檢查：** Internet Explorer 10 包括所有文字方塊的拼寫檢查功能。 這樣可讓您從建議的更正清單中選擇。 自動程式碼 UI 測試會忽略選取替代拼字建議之類的使用者動作。 只會記錄在文字方塊中輸入的最後一個字。<br />     會記錄使用拼字檢查控制項之自動程式碼 UI 測試的下列動作：[新增至字典]、[複製]、[全選]、[新增至字典] 和 [忽略]。<br />-   **支援在 Windows 8 下運行的 64 位 Internet 資源管理器：** 以前，64 位版本的 Internet Explorer 不支援錄製和播放。 在 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]中，已針對 Internet Explorer 64 位元版本啟用自動程式碼 UI 測試。 **警告：**      只有在執行 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本時，才會提供對 Internet Explorer 的 64 位元支援。<br />-   **支援 Internet 資源管理器中的固定網站 9：** 在 Internet 資源管理器 9 中，引入了固定網站。 使用釘選的網站時，您可直接從 Windows 工作列進入最喜愛的網站，而不需先開啟 Internet Explorer。 自動程式碼 UI 測試目前可以在釘選的網站上產生意圖感知動作。 有關固定網站的詳細資訊，請參閱[固定網站](https://support.microsoft.com/hub/4230784/internet-explorer-help)。<br />-   **支援 Internet 資源管理器 9 語義標記：** Internet Explorer 9 引入了以下語義標記：節、導航、文章、一旁、hgroup、標題、頁腳、圖、圖和標記。 自動程式碼 UI 測試會在錄製時忽略以上所有語意標記。 您可以使用 [自動程式碼 UI 測試產生器] 在這些標記上加入判斷提示。 您可以在 [自動程式碼 UI 測試產生器] 中使用巡覽撥號，巡覽至其中任何項目並檢視其屬性。<br />-   **在 Internet 資源管理器版本之間無縫處理空白字元：** Internet Explorer 8、IEExplorer 9 和 Internet Explorer 10 在空白字元的處理上存在差異。 自動程式碼 UI 測試會順暢地處理這些差異。 因此，在 Internet Explorer 8 中建立的自動程式碼 UI 測試可以在 Internet Explorer 9 和 Internet Explorer 10 中順利運作。<br />-   **現在，使用"錯誤時繼續"屬性集記錄 Internet 資源管理器的通知區域：** 現在，Internet Explorer 通知區域上的所有操作都使用"錯誤時繼續"屬性集進行記錄。 如果通知列未在播放期間出現，則會忽略其上面的動作，而自動程式碼 UI 測試會繼續執行下一個動作。 |
| Windows Forms 與 WPF 協力廠商控制項 | 完全支援。<br /><br /> 若要啟用 Windows Forms 和 WPF 應用程式的協力廠商控制項，您必須加入參考和程式碼。 有關詳細資訊，請參閱[啟用控制項的編碼 UI 測試](../test/enable-coded-ui-testing-of-your-controls.md)。 |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | 不支援。 |
| Chrome<br /><br /> Firefox | 不支援記錄動作步驟。 裝有 Visual Studio 2012 Update 4 或更新版本的 Chrome 和 Firefox 瀏覽器可以播放自動程式碼 UI 測試。 如需詳細資訊，請參閱 [這裡](using-different-web-browsers-with-coded-ui-tests.md) 。 |
| Opera<br /><br /> Safari | 不支援。 |
| Silverlight | 不支援。<br /><br /> 但是，對於 Visual Studo 2013，您可以從視覺工作室庫下載[Microsoft Visual Studio 2013 編碼的 UI 測試外掛程式，用於銀光](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve)。 |
| Flash/Java | 不支援。 |
| Windows Forms 2.0 和更新版本 | 完全支援。 **注意：**  完整支援 NetFx 控制項，但並未支援所有協力廠商控制項。 |
| WPF 3.5 和更新版本 | 完全支援。<br /><br /> **注意**NetFx 控制項完全支援，但並非所有協力廠商控制項都受支援。 |
| Windows Win32 | 使用時可能會出現某些已知問題，且未正式支援。 |
| MFC | 部分支援。 請參閱[UITest 架構](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) \(英文\) 以取 得支援之功能的詳細資料。 |
| SharePoint | 完全支援。 |
| Office 用戶端應用程式 | 不支援。 |
| Dynamics CRM Web 用戶端 | 完全支援。 |
| Dynamics (Ax) 2012 用戶端 | 部分支援動作記錄和播放。 有關詳細資訊[，請參閱 Visual Studio 10 編碼的 UI / 動作記錄支援。](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) |
| SAP | 不支援。 |
| Citrix/終端機服務 | 我們不建議在終端機伺服器上錄製動作。 錄製器不支援同時執行多個執行個體。 |
| PowerBuilder | 部分支援。<br /><br /> 支援的程度相當於啟用 PowerBuilder 控制項的協助工具。 |

如需如何建立延伸模組以支援其他平台的資訊，請參閱[啟用控制項的自動程式化 UI 測試](../test/enable-coded-ui-testing-of-your-controls.md)和[擴充自動程式化 UI 測試和動作記錄](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)。

## <a name="see-also"></a>另請參閱

- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
