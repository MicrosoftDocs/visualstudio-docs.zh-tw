---
title: 效能工作階段屬性 | Microsoft Docs
description: 瞭解效能會話如何讓您設定決定如何分析應用程式的設定。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 02ddf15251cf40dd340465563068b114940f9318
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721225"
---
# <a name="performance-session-properties"></a>效能工作階段屬性

[效能工作階段] 可以讓您進行設定，以決定如何對應用程式進行程式碼剖析。 它也會儲存針對程式碼剖析工作階段所產生的報告。

您可以執行 [效能精靈] 或手動建立工作階段，以建立 [效能工作階段]。 在 [效能工作階段] 建立完成後，[效能總管] 中便會顯示 [效能工作階段]。

若要檢視 [效能工作階段] 屬性，請在 [效能總管] 中選取工作階段名稱，以滑鼠右鍵按一下，然後選取 [屬性]。

效能工作階段具有下列屬性頁︰

## <a name="general"></a>一般

這些設定可以讓您選取程式碼剖析方法、加入 .NET 物件集合和存留期資料，和指定預設的報告位置和命名慣例。

如需詳細資訊，請參閱

[如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)

[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>啟動

這些設定可以讓您從二進位檔的清單中選擇，並指定二進位檔啟動的順序。

如需詳細資訊，請參閱[如何：指定要啟動的二進位](../profiling/how-to-specify-the-binary-to-start.md)檔。

## <a name="sampling"></a>取樣

這些設定可以讓您在使用取樣做為程式碼剖析方法時，選取取樣事件和取樣間隔。 取樣事件是用來依指定的間隔收集程式碼剖析資料。 例如，如果取樣事件是時脈週期，而取樣間隔設定為 10,000,000，則會在每一千萬個時時脈週期收集程式碼剖析資料。 有下列四種可用的取樣事件類型：

- 時脈週期 - 針對 CPU-bound 問題
- 分頁錯誤 - 針對記憶體相關問題
- 系統呼叫 - 針對 I/O 相關問題
- 效能計數器 - 針對低階效能問題
- 您可以根據可用的效能計數器來指定其他取樣事件

如需詳細資訊，請參閱 [如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>Binary
這些設定可以讓您指定是否要將已檢測的二進位檔重新配置到另一個位置。 例如，如果您要分析 *My.DLL* 並選擇不重新配置已檢測的二進位檔，則會建立名為 *My.Orig.DLL* *My.DLL* 的備份副本。 接著，藉由插入探查來收集資料來修改 *My.DLL* 。 如果您決定要重新配置已檢測的二進位檔，則不會重新命名原始二進位檔，而且會將已檢測的二進位檔複製到指定的位置供檢測期間使用。

如需詳細資訊，請參閱[如何：指定要啟動的二進位](../profiling/how-to-specify-the-binary-to-start.md)檔。

## <a name="tier-interactions"></a>階層互動

如需詳細資訊，請參閱[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>測試設備

這些設定可以讓您收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 網頁中 JScript 程式碼的效能資料，並指定您希望在檢測處理序前後發生的任何 [檢測前置] 和 [檢測後續] 事件。

如需詳細資訊，請參閱

[如何：分析網頁中的 JavaScript 程式碼](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[如何：指定檢測前置和檢測後續命令](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU 計數器

這些設定可讓您收集在使用檢測程式碼剖析方法時，有關 CPU 效能計數器的資料。 不論 CPU 設計或製造商為何，您都可以使用可移植的效能計數器。 平台事件需視 CPU 設計和製造商而定。 如需晶片上之效能計數器的詳細資訊，請參閱特定處理器的說明文件。

如需詳細資訊，請參閱 [如何：收集 CPU 計數器資料](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Windows 事件

在剖析期間，您可以收集來自事件追蹤提供者的資料。 您可以使用 [ *VSPerfReport.exe* 命令列工具] 選項來查看資料 `/calltrace` 。 如需 Windows 事件追蹤 (ETW) 的詳細資訊，請參閱[關於事件追蹤 (About Event Tracing)](/windows/win32/etw/about-event-tracing)。

如需詳細資訊，請參閱

[如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md)。

## <a name="windows-counters"></a>Windows 計數器

這個選項可以讓您從 Windows 效能監視器計數器收集資料。 若要收集此資料，請選取標記為 [收集 Windows 效能計數器] 的核取方塊。 收集的間隔時間可以在 [收集間隔] 方塊中設定。 另外，您可能也可以指定 [計數器分類] 和 [執行個體]。 部分預設 Windows 效能監視器計數器可供使用。

 如需詳細資訊，請參閱 [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)。

## <a name="advanced"></a>進階

這些設定可以讓您指定 [VSInstr](../profiling/vsinstr.md) 命令列程式碼剖析工具的一個或多個選項，便能將選項加入至檢測程序。 您也可以指定當應用程式使用超過一個以上版本時，要進行程式碼剖析的 Common Runtime 版本。

如需詳細資訊，請參閱

[如何：指定 .NET Framework 執行階段](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[如何：指定其他檢測選項](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>另請參閱

[概覽](../profiling/overviews-performance-tools.md) 
[設定效能會話](../profiling/configuring-performance-sessions.md) 
[控制資料收集](../profiling/controlling-data-collection.md)
