---
title: 使用檢測設備收集詳細計時資料
description: 流量分析工具檢測方法來取得程式碼區段的詳細計時資訊，以及瞭解 i/o 作業的影響。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17c569a9f5a50b769af0881d47fe810afe18058e
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533845"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>使用檢測設備收集詳細計時資料
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具檢測方法會將程式碼剖析的程式碼插入模組的複本。 執行剖析期間，程式碼會記錄在模組中函式的每個項目、結束和函式呼叫。 此檢測方法適合用來收集程式碼區段的詳細計時資訊，以及了解輸入和輸出作業對應用程式效能的影響。

 您可以使用下列程序的其中一個來指定檢測方法：

- 在 [程式碼剖析精靈] 的第一頁，選取 [檢測] 。

- 在 [效能總管]  工具列的 [方法]  清單中，按一下 [檢測] 。

- 在效能工作階段 [屬性] 對話方塊中的 [一般]  頁面，選取 [檢測] 。

## <a name="common-tasks"></a>常見工作
 您可以在效能會話的 [_效能會話_]**屬性頁** 對話方塊中指定其他選項。 若要開啟此對話方塊：

- 在 **效能總管** 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 [屬性] 。

  下表中的工作描述當您使用檢測方法進行分析時，可以在 [ _效能會話_**屬性頁** ] 對話方塊中指定的選項。

|工作|相關內容|
|----------|---------------------|
|在 [一般]  頁面，加入 .NET 記憶體配置和存留期資料，並指定產生的程式碼剖析資料 (.vsp) 檔案的命名詳細資料。|-   [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|
|在 [啟動]  頁面上，如果在您的方案中有多個 .exe 專案，請指定要啟動的應用程式和其啟動順序。|-   [如何：指定要啟動的二進位檔](../profiling/how-to-specify-the-binary-to-start.md)|
|在 [二進位檔]  頁面上，請指定此模組已檢測複本的位置。 根據預設，會將原始二進位碼檔案移到備份資料夾中。|-   [如何：重新放置檢測的二進位檔](../profiling/how-to-relocate-instrumented-binaries.md)|
|在 [階層互動]  頁面上，將 ADO.NET 呼叫資料加入程式碼剖析執行。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|
|在 [檢測]  頁面上，從程式碼剖析排除小型函式，以減少程式碼剖析額外負荷，而且排除在 ASP.NET 網頁的設定檔 JavaScript 程式碼，並指定要在檢測程序之前和之後於命令提示字元執行的命令。|-   [如何：從檢測排除或包含精簡函式](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [如何：分析網頁中的 JavaScript 程式碼](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [如何：指定檢測前置和檢測後續命令](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|在 [CPU 計數器]  頁面上，指定將加入程式碼剖析資料的一或多個處理器效能計數器。|-   [如何：收集 CPU 計數器資料](../profiling/how-to-collect-cpu-counter-data.md)|
|在 [Windows 事件]  頁面上，選取 Windows (ETW) 事件的一或多個事件追蹤，以收集取樣資料。|-   [如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|在 [Windows 計數器]  頁面上，指定將加入程式碼剖析資料為標記的一或多個作業系統效能計數器。|-   [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|
|在 [進階]  頁面上，指定您想要傳遞給 VSInstr 檢測程式的任何其他選項，例如要包含或排除特定的功能選項。|-   [如何：指定其他檢測選項](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
