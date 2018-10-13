---
title: IntelliTrace |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 882b8bd2e44bb630f70efe93a1338b8dd21dc501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228575"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) 。  
  
當您使用 IntelliTrace 記錄和追蹤程式碼的執行歷程時，可以縮短對應用程式進行偵錯的時間。 您可以輕鬆地找到錯誤，因為 IntelliTrace 可讓您：  
  
-   記錄特定事件  
  
     檢查相關的程式碼，會出現在的資料**區域變數**期間偵錯工具事件和函式呼叫資訊 視窗  
  
-   偵錯難以重現或在部署中所發生的錯誤  
  
 您可以在 Visual Studio Enterprise 版本 (而非 Professional 或 Community 版本) 中使用 IntelliTrace。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
|||  
|-|-|  
|**我的應用程式，使用 IntelliTrace 進行偵錯：**<br /><br /> -顯示過去的事件。<br />-顯示呼叫過去事件的資訊。<br />-儲存 IntelliTrace 工作階段。<br />控制 IntelliTrace 所收集的資料。|-   [逐步解說： 使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [IntelliTrace 功能](../debugger/intellitrace-features.md)<br />-   [設定 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [歷程偵錯](../debugger/historical-debugging.md)|  
|**在 Test Manager 中的測試工作階段期間收集 IntelliTrace 資料**|-   [收集更多診斷資料，在手動測試中](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**從已部署應用程式收集 IntelliTrace 資料**|-   [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**從開始偵錯的 IntelliTrace 記錄檔 （.iTrace 檔案）。**|-   [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a> 哪些應用程式偵錯使用 IntelliTrace？  
  
|||  
|-|-|  
|**支援**|-Visual Basic 和 Visual C# 應用程式使用.NET Framework 2.0 或更新版本。<br />     您可以偵錯大部分應用程式，包括 ASP.NET、Microsoft Azure、Windows Form、WCF、WPF、Windows Workflow、SharePoint 2010、SharePoint 2013 和 64 位元應用程式。<br />     若要偵錯 SharePoint 應用程式，使用 IntelliTrace，請參閱[逐步解說： 偵錯 SharePoint 應用程式所使用 IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)。<br />     若要使用 IntelliTrace 的 Microsoft Azure 應用程式進行偵錯，請參閱[偵錯已發佈的雲端服務使用 IntelliTrace 和 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248)。|  
|**有限的支援**|-F # 實驗基礎的應用程式<br />-Windows 市集應用程式支援僅適用於事件|  
|**不支援**|-C + +、 其他語言和指令碼<br />-Windows 服務、 Silverlight、 Xbox 或[!INCLUDE[winmobile](../includes/winmobile-md.md)]應用程式|  
  
> [!NOTE]
>  如果您要偵錯已在執行中的處理序，則不能使用 IntelliTrace。 您必須在處理序啟動時啟動 IntelliTrace。  
  
##  <a name="IntelliTraceVSTraditional"></a> 為什麼要使用 IntelliTrace 偵錯嗎？  
 傳統或*live*偵錯只會顯示您的應用程式目前狀態，有關過去事件的有限資料。 您必須根據應用程式的目前狀態來推斷這些事件，或者必須透過重新執行應用程式來重新建立這些事件。  
  
 IntelliTrace 透過記錄在這些時間點的特定事件和資料，擴展了這個傳統的偵錯經驗。 這可讓您查看應用程式中發生的事件，而不需要重新啟動它，特別是如果您已逐步執行超過 Bug 的位置時。 在傳統偵錯期間，IntelliTrace 預設會開啟並以隱藏的方式自動收集資料。 這可讓您輕易地切換傳統偵錯和 IntelliTrace 偵錯，以查看所記錄的資訊。 請參閱[IntelliTrace 功能](../debugger/intellitrace-features.md)和[IntelliTrace 會收集哪些資料？](#WhatData)  
  
 IntelliTrace 也可協助您偵錯難以重現或在部署中發生的錯誤。 您可以收集 IntelliTrace 資料並將其儲存至 IntelliTrace 記錄檔 (.iTrace 檔案)。 .iTrace 檔案包含有關例外狀況、效能事件、Web 要求、測試資料、執行緒、模組和其他系統資訊的詳細資料。 您可以在 Visual Studio Enterprise 中開啟這個檔案，並選取某個項目，然後使用 IntelliTrace 開始偵錯。 這可讓您移至檔案中的任何事件，並查看應用程式在該時間點的特定詳細資料。  
  
 您可以儲存來自下面這些來源的 IntelliTrace 資料：  
  
-   在 Visual Studio 2015 Enterprise 或舊版的 Visual Studio Ultimate 中的 IntelliTrace 工作階段。  
  
-   Microsoft Test Manager 中的測試工作階段  
  
-   如果是使用 Microsoft Monitoring Agent (獨立執行或搭配 System Center 2012 運作)，則為裝載於 IIS 上的 ASP.NET Web 應用程式或是在部署中執行的 SharePoint 2010 和 SharePoint 2013 應用程式。 請參閱[使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)並[監視使用 Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx)。  
  
 下面是一些 IntelliTrace 如何協助您偵錯的範例：  
  
-   您的應用程式含有損毀的資料檔，但您不知道此事件在何處發生。  
  
     如果沒有 IntelliTrace，您就必須逐一查看程式碼來尋找所有可能的檔案存取、在這些存取上放置中斷點，然後重新執行應用程式來找出發生問題的位置。 如果有 IntelliTrace，您就可以看到所有收集的檔案存取事件，以及在每個事件發生時應用程式的特定詳細資訊。  
  
-   發生例外狀況。  
  
     如果沒有 IntelliTrace，您會收到有關例外狀況的訊息，但沒有很多關於造成例外狀況的事件的資訊。 雖然您可以檢查呼叫堆疊來查看導致例外狀況的呼叫鏈結，但是卻看不到在這些呼叫期間所發生的事件順序。 如果有 IntelliTrace，您就可以查看在例外狀況之前所發生的事件。  
  
-   您的應用程式在測試電腦上當機，但在開發電腦上卻執行得很順利。  
  
     您可以從 Microsoft Test Manager 收集 IntelliTrace 資料，將資料儲存至 .iTrace 檔案，然後將這個檔案附加至 Team Foundation Server 工作項目供日後調查。 請參閱[收集詳細的診斷資料，在手動測試中](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)並[儲存的 IntelliTrace 資料的使用](../debugger/using-saved-intellitrace-data.md)。  
  
-   在部署的應用程式中發生 Bug 或當機。  
  
     如果是 Microsoft Azure 架構的應用程式，您可以在發行應用程式之前先設定 IntelliTrace 資料收集。 在應用程式執行的同時，IntelliTrace 會將資料儲存到 .iTrace 檔案。 請參閱[偵錯發佈的雲端服務使用 IntelliTrace 和 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248)。  
  
     如果是裝載於 IIS 7.0、7.5 和 8.0 上的 ASP.NET Web 應用程式，以及 SharePoint 2010 或 SharePoint 2013 應用程式，請使用 Microsoft Monitoring Agent (獨立執行或搭配 System Center 2012 運作) 來將 IntelliTrace 資料儲存到 .iTrace 檔案。  
  
     如果要診斷部署中的應用程式的問題時，這十分有用。 請參閱[使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
##  <a name="WhatData"></a> IntelliTrace 會收集哪些資料？  
 **收集事件資訊**  
  
 IntelliTrace 預設只會記錄 IntelliTrace 事件：偵錯工具事件、例外狀況、.NET Framework 事件，以及有助於偵錯的其他系統事件。 您可以選擇要收集的 IntelliTrace 事件種類 (除了偵錯工具事件和例外狀況外，這些項目一律會收集)。 請參閱[設定 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
-   **偵錯工具事件**  
  
     IntelliTrace 一律會記錄在 Visual Studio Debugger 中發生的事件。 例如，啟動您的應用程式就是一個偵錯工具事件。 其他偵錯工具事件包括停止事件，也就是導致應用程式中斷執行的事件。 您的程式，例如，叫用中斷點、 遇到了追蹤點，或執行**步驟**命令。  
  
     為了協助提高效能，IntelliTrace 不會記錄偵錯工具事件的每個可能的值。 相反地，它會記錄下面這些值：  
  
    -   中的值**區域變數**視窗。 保持**區域變數**視窗中開啟來查看這些值。  
  
    -   中的值**自動變數** 視窗才**自動變數**視窗已開啟  
  
    -   在您將滑鼠指標放置在來源視窗中的變數上方以查看它的值時，所出現的 DataTips 中的值。 IntelliTrace 不會收集固定的 DataTips 中的值。  
  
-   **例外狀況**  
  
     IntelliTrace 會記錄下列例外狀況種類的例外狀況類型和訊息：  
  
    -   已處理的例外狀況 (例外狀況已擲回並已攔截)  
  
    -   未處理的例外狀況  
  
-   **.NET framework 事件**  
  
     根據預設，IntelliTrace 會記錄最常見的 .NET Framework 事件。 例如：  
  
    -   如果是檔案存取事件，IntelliTrace 會收集檔案名稱。  
  
    -   如果是選取核取方塊事件，IntelliTrace 會收集核取方塊的狀態和文字。  
  
-   **SharePoint 2010 和 SharePoint 2013 應用程式事件**  
  
     您可以記錄在 Visual Studio 外部執行之 SharePoint 2010 和 2013 應用程式的使用者設定檔事件以及統一登入系統 (ULS) 事件的子集。 您可以將這些事件儲存成 .iTrace 檔案。 需要 Visual Studio Enterprise 2015、 舊版的 Visual Studio Ultimate 或[Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384)中執行**追蹤**模式。  
  
     當您開啟 .iTrace 檔案時，請輸入 SharePoint 相互關聯識別碼以尋找其相符的 Web 要求、檢視記錄的事件，並從特定事件開始偵錯。 如果檔案包含未處理的例外狀況，您可以選擇某個相互關聯識別碼，開始偵錯例外狀況。  
  
     請參閱：  
  
    -   [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
    -   [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)  
  
    -   [逐步解說：使用 IntelliTrace 偵錯 SharePoint 應用程式](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
 **收集函式呼叫資訊**  
  
 您可以設定讓 IntelliTrace 收集函式呼叫資訊。 這項資訊可讓您查看呼叫堆疊記錄，並讓您向後和向前逐步執行程式碼中的呼叫。 IntelliTrace 會針對每個函式呼叫記錄下列資料：  
  
-   函式名稱  
  
-   在函式進入點做為參數傳遞且在函式結束點傳回的基本資料類型值  
  
-   讀取或變更時的自動屬性的值  
  
-   第一層子物件的指標，但不含是否為 null 以外的值  
  
> [!NOTE]
>  IntelliTrace 只會收集陣列中的前 256 個物件以及字串的前 256 個字元。  
  
 請參閱[設定 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
 **收集模組資訊**  
  
 若要控制 IntelliTrace 收集呼叫資訊的數量，請僅指定您關心的模組。 這有助於改善應用程式在收集期間的效能。 請參閱[設定 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
##  <a name="AffectPerformance"></a> 將 IntelliTrace 應用程式變慢？  
 根據預設，IntelliTrace 只會針對選取的 IntelliTrace 事件收集資料。 根據程式碼的結構和組織，這不一定會讓您的應用程式變慢。 例如，如果 IntelliTrace 時常記錄某個事件，這可能會讓應用程式變慢。 它也可能會讓您考慮重構應用程式。  
  
 收集呼叫資訊可能會使應用程式明顯變慢， 也可能會增加要儲存至磁碟之任何 IntelliTrace 記錄檔 (.iTrace 檔案) 的大小。 若要將這些影響降至最低，請只針對您關注的那些模組收集呼叫資訊。  若要變更.iTrace 檔案的大小上限，請前往**工具**，**選項**， **IntelliTrace**，**進階**。 請參閱[設定 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
## <a name="in-this-section"></a>本節內容  
 [IntelliTrace 功能](../debugger/intellitrace-features.md)  
  
 [設定 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [包含難以重現的 bug 的診斷追蹤資料](http://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [於部署後診斷問題](../debugger/diagnose-problems-after-deployment.md)  
  
 [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>部落格  
 [Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>論壇  
 [Visual Studio 的診斷功能](http://go.microsoft.com/fwlink/?LinkId=262263)





