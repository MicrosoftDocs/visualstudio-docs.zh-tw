---
title: IntelliTrace | Microsoft Docs
description: 使用 IntelliTrace 在 Visual Studio 中記錄和追蹤程式碼的執行歷程記錄。 記錄特定事件、檢查相關的程式碼和偵錯工具錯誤。
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518043a38f3a0f6945840a36a1f7fcade5a313d7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148997"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>適用于 Visual Studio Enterprise (c #、Visual Basic、c + +) 的 IntelliTrace

當您使用 IntelliTrace 記錄和追蹤程式碼的執行歷程時，可以縮短對應用程式進行偵錯的時間。 您可以輕鬆地找到錯誤，因為 IntelliTrace 可讓您：

- 記錄特定事件

- 請檢查相關的程式碼、發生偵錯工具事件時出現在 [區域變數] 視窗中的資料，以及函式呼叫資訊

- 偵錯難以重現或在部署中所發生的錯誤

您可以在 Visual Studio Enterprise 版本 (而非 Professional 或 Community 版本) 中使用 IntelliTrace。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

|案例|標題|
|-|-|
|**使用 IntelliTrace 偵錯我的應用程式：**<br /><br /> - 顯示過去的事件。<br />- 顯示過去事件的呼叫資訊。<br />- 儲存 IntelliTrace 工作階段。<br />- 控制 IntelliTrace 收集的資料。|- [使用 IntelliTrace 檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)<br />- [逐步解說：使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace 功能](../debugger/intellitrace-features.md)<br />- [歷程記錄調試](../debugger/historical-debugging.md)|
|**從部署的應用程式中收集 IntelliTrace 資料**|- [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**從 IntelliTrace 記錄檔 (.iTrace 檔案) 開始偵錯。**|- [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)|

## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a>我可以使用 IntelliTrace 對哪些應用程式進行偵錯？

| 支援層級| 應用程式類型 |
|---------------------| - |
| **完整支援** | - 使用 .NET Framework 2.0 或更高版本的 Visual Basic 和 Visual C# 應用程式。<br/>您可以偵錯大部分應用程式，包括 ASP.NET、Microsoft Azure、Windows Form、WCF、WPF、Windows Workflow、SharePoint 2010、SharePoint 2013 和 64 位元應用程式。<br/>若要使用 IntelliTrace 來對 SharePoint 應用程式進行偵錯工具，請參閱 [逐步解說：使用 intellitrace 來偵測 Sharepoint 應用程式](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)。<br/> 若要使用 IntelliTrace 來進行 Microsoft Azure 應用程式的偵錯工具，請參閱 [使用 intellitrace 和 Visual Studio 來偵測已發佈的雲端服務](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md)。 |
| **有限支援** | -以 Windows 為目標的 c + + 應用程式支援使用 IntelliTrace 回溯查看快照集。 只支援偵錯工具和例外狀況事件。<br />-僅針對特定事件支援的 .NET Core 和 ASP.NET Core 應用程式 (MVC 控制器、ADO.NET 和 HTTPClient 事件) 在本機偵錯工具中。 .NET Core 或 ASP.NET Core 的應用程式不支援獨立收集器。<br />- 實驗基礎的 F# 應用程式<br />-僅支援事件的 UWP 應用程式 |
| **不支援** | -其他語言和腳本<br />-Windows 服務、Silverlight、Xbox 或 Windows Mobile 應用程式 |

> [!NOTE]
> 如果您想要將已經在執行中的處理常式進行偵錯工具，您只能收集 (沒有呼叫資訊) 的 IntelliTrace 事件。 您只能在本機電腦上附加至32位或64位進程。 不會收集您附加至進程之前發生的事件。

## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> 為什麼要使用 IntelliTrace 進行偵錯？

傳統或「即時」(Live) 偵錯只會顯示應用程式的目前狀態，並只包含有關過去事件的有限資料。 您必須根據應用程式的目前狀態來推斷這些事件，或者必須透過重新執行應用程式來重新建立這些事件。

IntelliTrace 透過記錄在這些時間點的特定事件和資料，擴展了這個傳統的偵錯經驗。 這可讓您查看應用程式中發生的事件，而不需要重新啟動它，特別是如果您已逐步執行超過 Bug 的位置時。 在傳統偵錯期間，IntelliTrace 預設會開啟並以隱藏的方式自動收集資料。 這可讓您輕易地切換傳統偵錯和 IntelliTrace 偵錯，以查看所記錄的資訊。 請參閱 [Intellitrace 功能](../debugger/intellitrace-features.md) 和 [intellitrace 收集哪些資料？](#WhatData)

IntelliTrace 也可協助您偵錯難以重現或在部署中發生的錯誤。 您可以收集 IntelliTrace 資料並將其儲存至 IntelliTrace 記錄檔 (.iTrace 檔案)。 .iTrace 檔案包含有關例外狀況、效能事件、Web 要求、測試資料、執行緒、模組和其他系統資訊的詳細資料。 您可以在 Visual Studio Enterprise 中開啟這個檔案，並選取某個項目，然後使用 IntelliTrace 開始偵錯。 這可讓您移至檔案中的任何事件，並查看應用程式在該時間點的特定詳細資料。

您可以儲存來自下面這些來源的 IntelliTrace 資料：

- Visual Studio 2015 Enterprise 或更新版本中的 IntelliTrace 會話，或舊版的 Visual Studio Ultimate。

- 如果是使用 Microsoft Monitoring Agent (獨立執行或搭配 System Center 2012 運作)，則為裝載於 IIS 上的 ASP.NET Web 應用程式或是在部署中執行的 SharePoint 2010 和 SharePoint 2013 應用程式。 請參閱 [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md) 和 [監視 Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12))。

下面是一些 IntelliTrace 如何協助您偵錯的範例：

- 您的應用程式含有損毀的資料檔，但您不知道此事件在何處發生。

  如果沒有 IntelliTrace，您就必須逐一查看程式碼來尋找所有可能的檔案存取、在這些存取上放置中斷點，然後重新執行應用程式來找出發生問題的位置。 如果有 IntelliTrace，您就可以看到所有收集的檔案存取事件，以及在每個事件發生時應用程式的特定詳細資訊。

- 發生例外狀況。

  如果沒有 IntelliTrace，您會收到有關例外狀況的訊息，但沒有很多關於造成例外狀況之事件的資訊。 雖然您可以檢查呼叫堆疊來查看導致例外狀況的呼叫鏈結，但是卻看不到在這些呼叫期間所發生的事件順序。 如果有 IntelliTrace，您就可以查看在例外狀況之前所發生的事件。

- 在部署的應用程式中發生 Bug 或當機。

  如果是 Microsoft Azure 架構的應用程式，您可以在發行應用程式之前先設定 IntelliTrace 資料收集。 在應用程式執行的同時，IntelliTrace 會將資料儲存到 .iTrace 檔案。 請參閱 [使用 IntelliTrace 和 Visual Studio 來調試已發佈的雲端服務](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md)。

  如果是裝載於 IIS 7.0、7.5 和 8.0 上的 ASP.NET Web 應用程式，以及 SharePoint 2010 或 SharePoint 2013 應用程式，請使用 Microsoft Monitoring Agent (獨立執行或搭配 System Center 2012 運作) 來將 IntelliTrace 資料儲存到 .iTrace 檔案。

  如果要診斷部署中的應用程式的問題時，這十分有用。 請參閱 [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。

## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> IntelliTrace 會收集哪些資料？

**收集事件資訊**

IntelliTrace 預設只會記錄 IntelliTrace 事件：偵錯工具事件、例外狀況、.NET Framework 事件，以及有助於偵錯的其他系統事件。 您可以選擇要收集的 IntelliTrace 事件種類 (除了偵錯工具事件和例外狀況外，這些項目一律會收集)。 請參閱 [IntelliTrace 功能](../debugger/intellitrace-features.md)。

- **偵錯工具事件**

  IntelliTrace 一律會記錄在 Visual Studio Debugger 中發生的事件。 例如，啟動您的應用程式就是一個偵錯工具事件。 其他偵錯工具事件包括停止事件，也就是導致應用程式中斷執行的事件。 例如，您的程式遇到了中斷點、遇到了追蹤點或執行 [逐步執行] 命令時。

  根據預設，若要協助效能，IntelliTrace 不會記錄偵錯工具事件的每個可能值。 相反地，它會記錄下面這些值：

  - [區域變數] 視窗中的值。 讓 [區域變數] 視窗保持開啟來查看這些值。

  - [自動變數] 視窗中的值 (只有當 [自動變數] 視窗開啟時)

  - 在您將滑鼠指標放置在來源視窗中的變數上方以查看它的值時，所出現的 DataTips 中的值。 IntelliTrace 不會收集固定的 DataTips 中的值。

    當 IntelliTrace 事件和快照模式啟用時，IntelliTrace 會在每個偵錯工具 **中斷點** 和 **步驟** 事件中取得應用程式進程的快照集。 這會記錄 [區域變數]、[自動 **變數**] 和 [**監看式]** 視窗中的值，而不論視窗是否開啟。  也會收集任何釘選資料提示中的值。

- **例外狀況**

  IntelliTrace 會記錄下列例外狀況種類的例外狀況類型和訊息：

  - 已處理的例外狀況 (例外狀況已擲回並已攔截)

  - 未處理的例外狀況

- **.NET Framework 事件**

  根據預設，IntelliTrace 會記錄最常見的 .NET Framework 事件。 例如，針對 <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> 事件，IntelliTrace 會收集核取方塊的狀態和文字。

- **SharePoint 2010 和 SharePoint 2013 應用程式事件**

  您可以記錄在 Visual Studio 外部執行之 SharePoint 2010 和 2013 應用程式的使用者設定檔事件以及統一登入系統 (ULS) 事件的子集。 您可以將這些事件儲存成 .iTrace 檔案。 需要 Visual Studio Enterprise 2015 或更新版本、舊版 Visual Studio Ultimate，或在 **追蹤** 模式下執行 [Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316) 。

  當您開啟 .iTrace 檔案時，請輸入 SharePoint 相互關聯識別碼以尋找其相符的 Web 要求、檢視記錄的事件，並從特定事件開始偵錯。 如果檔案包含未處理的例外狀況，您可以選擇某個相互關聯識別碼，開始偵錯例外狀況。

  請參閱：

  - [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)

  - [逐步解說：使用 IntelliTrace 針對 SharePoint 應用程式進行偵錯](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**捕捉快照集**

您可以設定 IntelliTrace，以在每個中斷點和偵錯工具步驟事件中捕捉快照集。 IntelliTrace 會在每個快照集上記錄完整的應用程式狀態，讓您能夠查看複雜變數和評估運算式。

> [!NOTE]
> [IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)不支援捕獲快照集。

請參閱 [使用 IntelliTrace 檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)。

**收集函式呼叫資訊**

您可以設定讓 IntelliTrace 收集函式呼叫資訊。 這項資訊可讓您查看呼叫堆疊記錄，並讓您向後和向前逐步執行程式碼中的呼叫。 IntelliTrace 會針對每個函式呼叫記錄下列資料：

- 函式名稱
- 在函式進入點做為參數傳遞且在函式結束點傳回的基本資料類型值
- 讀取或變更時的自動屬性的值
- 第一層子物件的指標，但不含是否為 null 以外的值

> [!NOTE]
> IntelliTrace 只會收集陣列中的前 256 個物件以及字串的前 256 個字元。

請參閱 [使用歷程記錄偵測檢查您的應用程式](../debugger/historical-debugging-inspect-app.md)。

**收集模組資訊**

若要控制 IntelliTrace 收集呼叫資訊的數量，請僅指定您關心的模組。 這有助於改善應用程式在收集期間的效能。 請參閱一節，以控制 IntelliTrace 在 IntelliTrace 功能中 [收集的資訊量](../debugger/intellitrace-features.md#ControlCallData) 。

## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> IntelliTrace 是否會讓應用程式變慢？

根據預設，IntelliTrace 只會針對選取的 IntelliTrace 事件收集資料。 根據程式碼的結構和組織，這不一定會讓您的應用程式變慢。 例如，如果 IntelliTrace 時常記錄某個事件，這可能會讓應用程式變慢。 它也可能會讓您考慮重構應用程式。

收集呼叫資訊可能會使應用程式明顯變慢， 也可能會增加要儲存至磁碟之任何 IntelliTrace 記錄檔 (.iTrace 檔案) 的大小。 若要將這些影響降至最低，請只針對您關注的那些模組收集呼叫資訊。  若要變更 .iTrace 檔案的大小上限，請移至 [工具]、[選項]、[IntelliTrace]、[進階]。

### <a name="blogs"></a>部落格

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>論壇

[Visual Studio 的診斷功能](https://social.msdn.microsoft.com/Forums/en-US/home)