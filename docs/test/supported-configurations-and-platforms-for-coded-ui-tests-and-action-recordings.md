---
title: Visual Studio 中自動程式化 UI 測試的組態和平台
ms.date: 2015-10-04
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 65b28ed774c9e0e17f1901a4d13eadbaddf39884
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510984"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>自動程式碼 UI 測試和動作記錄的支援組態和平台

Visual Studio 企業版的自動程式碼 UI 測試的支援組態與平台會列在下表中。 這些組態也套用至使用 [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]建立的動作記錄。

> [!NOTE]
> 自動程式碼 UI 測試處理序的權限必須和待測 App 的權限相同。


 **需求**

-   Visual Studio 企業版

## <a name="supported-configurations"></a>支援的設定

|Configuration|支援|
|-------------------|---------------|
|作業系統|[!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10|
|32 位元/ 64 位元支援|執行 32 位元 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 的 32 位元 Windows 可以測試 32 位元應用程式。<br /><br /> 執行 32 位元 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 的 64 位元 Windows，可以測試具有「UI 同步處理」的 32 位元 WOW 應用程式。<br /><br /> 執行 32 位元 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 的 64 位元 Windows 可以測試沒有「UI 同步處理」的 64 位元 Windows Form 和 WPF 應用程式。|
|架構|x86 和 x64 **注意事項：** 除非在 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本執行，否則 64 位元模式不支援 Internet Explorer。|
|.NET|.NET 2.0、3.0、3.5、4 和 4.5。 **注意：**[!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 和 Visual Studio 都需要 .NET 4 才能運作。 然而，支援使用列出的 .NET 版本開發的應用程式。|

> [!NOTE]
> 「*UI 同步處理* 」(UI Synchronization) 功能可在每個控制項的訊息佇列中驗證播放。 如果控制項沒有回應傳送至它的事件，則會重新傳送事件。


## <a name="platform-support"></a>平台支援

|Platform|支援層級|
|--------------|----------------------|
|Windows Phone App|只支援 WinRT-XAML 架構的 Phone 應用程式。|
|UWP 應用程式|只支援以 XAML 為基礎 UWP 的應用程式。|
|通用 Windows App|只支援手機和桌上型電腦上以 XAML 為基礎的通用 Windows App。|
|Edge|不支援錄製動作步驟或使用產生器來檢視物件屬性。 使用 Visual Studio 2015 Update 2 和更新版本可以在 Edge 瀏覽器上播放測試，方法是使用[自動程式化 UI 跨瀏覽器測試延伸模組](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **重要事項︰** 只有在桌上型電腦才支援 Internet Explorer 10。 <br /><br /> Internet Explorer 11 **重要事項︰** 只有在桌上型電腦才支援 Internet Explorer 11。|完全支援。<br /><br /> -   **在 Internet Explorer 9 和 Internet Explorer 10 中支援 HTML5：** 自動程式碼 UI 測試支援錄製、播放和驗證 HTML5 控制項：Audio、Video、ProgressBar 和 Slider。 如需詳細資訊，請參閱[在自動程式化 UI 測試中使用 HTML5 控制項](../test/using-html5-controls-in-coded-ui-tests.md)。 **警告：**      如果您在 Internet Explorer 10 中建立自動程式化 UI 測試，可能無法使用 Internet Explorer 9 或 Internet Explorer 8 執行。 這是因為 Internet Explorer 10 包含 HTML5 控制項，例如 Audio、Video、ProgressBar 和 Slider。 Internet Explorer 9 或 Internet Explorer 8 無法辨識這些 HTML5 控制項。 同樣地，使用 Internet Explorer 9 的自動程式碼 UI 測試可能包含一些 Internet Explorer 8 無法辨識的 HTML5 控制項。<br />-   **支援 Internet Explorer 10 拼字檢查：** Internet Explorer 10 包含所有文字方塊的拼字檢查功能。 這樣可讓您從建議的更正清單中選擇。 自動程式碼 UI 測試會忽略選取替代拼字建議之類的使用者動作。 只會記錄在文字方塊中輸入的最後一個字。<br />     會記錄使用拼字檢查控制項之自動程式碼 UI 測試的下列動作：[新增至字典]、[複製]、[全選]、[新增至字典] 和 [忽略]。<br />-   **支援在 Windows 8 下執行的 64 位元 Internet Explorer：** 之前並不支援使用 64 位元版本的 Internet Explorer 進行錄製和播放。 在 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，已針對 Internet Explorer 64 位元版本啟用自動程式碼 UI 測試。 **警告：**      只有在執行 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本時，才會提供對 Internet Explorer 的 64 位元支援。<br />-   **在 Internet Explorer 9 中支援釘選的網站：** Internet Explorer 9 已導入釘選的網站。 使用釘選的網站時，您可直接從 Windows 工作列進入最喜愛的網站，而不需先開啟 Internet Explorer。 自動程式碼 UI 測試目前可以在釘選的網站上產生意圖感知動作。 如需釘選網站的詳細資訊，請參閱[釘選的網站](http://go.microsoft.com/fwlink/?LinkId=220037)。<br />-   **支援 Internet Explorer 9 語意標記：** Internet Explorer 9 引進了下列語意標記：section、nav、article、aside、hgroup、header、footer、figure、figcaption 和 mark。 自動程式碼 UI 測試會在錄製時忽略以上所有語意標記。 您可以使用 [自動程式碼 UI 測試產生器] 在這些標記上加入判斷提示。 您可以在 [自動程式碼 UI 測試產生器] 中使用巡覽撥號，巡覽至其中任何項目並檢視其屬性。<br />-   **完美地處理在 Internet Explorer 版本之間的空白字元：** Internet Explorer 8、Internet Explorer 9 和 Internet Explorer 10 處理空白字元的方式有所差異。 自動程式碼 UI 測試會順暢地處理這些差異。 因此，在 Internet Explorer 8 中建立的自動程式碼 UI 測試可以在 Internet Explorer 9 和 Internet Explorer 10 中順利運作。<br />-   **現在會記錄 Internet Explorer 的通知區域並且設定「錯誤時繼續」屬性：** 在 Internet Explorer 通知區域中的所有動作現在都會加以記錄，並且會設定「錯誤時繼續」屬性。 如果通知列未在播放期間出現，則會忽略其上面的動作，而自動程式碼 UI 測試會繼續執行下一個動作。|
|Windows Forms 與 WPF 協力廠商控制項|完全支援。<br /><br /> 若要啟用 Windows Forms 和 WPF 應用程式的協力廠商控制項，您必須加入參考和程式碼。 如需詳細資訊，請參閱[啟用控制項的自動程式化 UI 測試](../test/enable-coded-ui-testing-of-your-controls.md)。|
|Internet Explorer 6<br /><br /> Internet Explorer 7|不支援。|
|Chrome<br /><br /> Firefox|不支援記錄動作步驟。 裝有 Visual Studio 2012 Update 4 或更新版本的 Chrome 和 Firefox 瀏覽器可以播放自動程式碼 UI 測試。 如需詳細資訊，請參閱 [這裡](using-different-web-browsers-with-coded-ui-tests.md) 。|
|Opera<br /><br /> Safari|不支援。|
|Silverlight|不支援。<br /><br /> 不過針對 Visual Studo 2013，您可以從 Visual Studio 組件庫下載[適用於 Silverlight 的 Microsoft Visual Studio 2013 自動程式化 UI 測試外掛程式](https://go.microsoft.com/fwlink/?LinkId=691026)。|
|Flash/Java|不支援。|
|Windows Forms 2.0 和更新版本|完全支援。 **注意：**  完整支援 NetFx 控制項，但並未支援所有協力廠商控制項。|
|WPF 3.5 和更新版本|完全支援。<br /><br /> **注意** 完全支援 NetFx 控制項，但並非所有協力廠商控制項都可支援。|
|Windows Win32|使用時可能會出現某些已知問題，且未正式支援。|
|MFC|部分支援。 請參閱[UITest 架構](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) \(英文\) 以取 得支援之功能的詳細資料。|
|SharePoint|完全支援。|
|Office 用戶端應用程式|不支援。|
|Dynamics CRM Web 用戶端|完全支援。|
|Dynamics (Ax) 2012 用戶端|部分支援動作記錄和播放。 如需詳細資訊，請參閱 [Visual Studio 10 coded UI / action recordings support for Microsoft Dynamics](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) (Visual Studio 10 針對 Microsoft Dynamics 的自動程式化 UI/動作記錄支援)。|
|SAP|不支援。|
|Citrix/終端機服務|我們不建議在終端機伺服器上錄製動作。 錄製器不支援同時執行多個執行個體。|
|PowerBuilder|部分支援。<br /><br /> 支援的程度相當於啟用 PowerBuilder 控制項的協助工具。|

 如需如何建立延伸模組以支援其他平台的資訊，請參閱[啟用控制項的自動程式化 UI 測試](../test/enable-coded-ui-testing-of-your-controls.md)和[擴充自動程式化 UI 測試和動作記錄](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)。

## <a name="see-also"></a>另請參閱

- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
