---
title: 收集 .NET 記憶體配置 & 存留期資料
description: 若要協助偵測 .NET 應用程式中記憶體相關的效能問題，請流量分析工具來收集記憶體配置和物件存留期資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 00a8b7c7e92153fcbc323349f30adc458cf973fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839279"
---
# <a name="collect-net-framework-memory-allocation-and-lifetime-data"></a>收集 .NET Framework 記憶體配置和存留期資料

Visual Studio 分析工具支援 .NET Framework 記憶體配置和物件存留期資料的集合，可協助您偵測應用程式中與記憶體相關的效能問題。

- 與 .NET 記憶體配置相關的資料包括所配置的 .NET Framework 記憶體物件的大小與數目。

- 物件存留期資料包含在三個記憶體回收層代中回收之 .NET Framework 記憶體物件的大小和數目。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

您可以使用取樣或檢測分析方法來收集資料。

- 當您使用取樣方法時，分析工具會追蹤由啟動或附加的處理序所產生的所有 .NET 記憶體配置和物件。

- 當您使用檢測方法時，分析工具會追蹤由檢測模組所產生的 .NET 記憶體配置和物件。

> [!IMPORTANT]
> 當您使用取樣方法收集 .NET 記憶體資料 (配置、物件存留期，或兩者)，則會忽略所有使用者指定的取樣事件，並使用適當的記憶體配置事件來收集資料。

如果您啟用 .NET 記憶體配置的分析，也可以啟用 [配置檢視]。 如果您啟用 .NET 存留期資料的分析，也可以啟用 [物件存留期檢視]。 如需詳細資訊，請參閱[配置檢視](../profiling/dotnet-memory-allocations-view.md)和[物件存留期檢視](../profiling/object-lifetime-view.md)。

如需如何使用分析工具命令列工具收集 .NET 記憶體資料的相關資訊，請參閱[從命令列使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)中的＜使用 .NET 記憶體方法收集記憶體配置和物件存留期資料＞。

## <a name="to-collect-net-memory-data"></a>收集 .NET 記憶體資料

1. 在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。

2. 在 [效能工作階段屬性頁]  對話方塊中，按一下 [一般] 索引標籤，並選取 [收集 .NET 物件配置資訊] 核取方塊。

3. 若要收集 .NET 物件存留期資料，請選取 [同時收集 .NET 物件存留期的資訊] 核取方塊。

## <a name="common-tasks"></a>常見工作

您可以在效能會話的 [_效能會話_]**屬性頁** 對話方塊中指定其他選項。 若要開啟此對話方塊：

- 在 **效能總管** 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 [屬性] 。

下表中的工作說明當您收集 .NET 記憶體資料時，可以在 [效能工作階段屬性頁] 對話方塊中指定的選項。

|Task|相關內容|
|----------|---------------------|
|在 [一般] 頁面上，指定產生的分析資料 (.vsp) 檔案的命名詳細資料。|- [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|
|在 [啟動] 頁面上，如果您的程式碼方案中有多個 .exe 專案，請選擇要啟動的應用程式。|- [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|
|在 [階層互動]  頁面上，將 ADO.NET 呼叫資料加入程式碼剖析執行。|- [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|
|在 [Windows 事件] 頁面上，指定一或多個要收集取樣資料的 Windows 事件追蹤 (ETW) 事件。|- [如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|在 [Windows 計數器]  頁面上，指定將加入程式碼剖析資料為標記的一或多個作業系統效能計數器。|- [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|
|在 [進階] 頁面上，如果您的應用程式模組使用多個版本，請指定要分析的 .NET Framework 執行階段版本。 預設會分析載入的第一個版本。|- [如何：指定 .NET Framework 執行時間](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>檢測工作

下表中的工作是 [屬性頁] 對話方塊中使用檢測方法進行分析的特定選項。

|Task|相關內容|
|----------|---------------------|
|在 [二進位檔]  頁面上，請指定此模組已檢測複本的位置。 根據預設，會將原始二進位碼檔案移到備份資料夾中。|- [如何：重新放置檢測的二進位檔](../profiling/how-to-relocate-instrumented-binaries.md)|
|在 [檢測]  頁面上，從程式碼剖析排除小型函式，以減少程式碼剖析額外負荷，而且排除在 ASP.NET 網頁的設定檔 JavaScript 程式碼，並指定要在檢測程序之前和之後於命令提示字元執行的命令。|- [如何：從檢測排除或包含精簡函式](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [如何：分析網頁中的 JavaScript 程式碼](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [如何：指定檢測前置和檢測後續命令](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|在 [CPU 計數器]  頁面上，指定將加入程式碼剖析資料的一或多個處理器效能計數器。|- [如何：收集 CPU 計數器資料](../profiling/how-to-collect-cpu-counter-data.md)|
|在 [進階] 頁面上，指定您想要的任何其他 VSInstr.exe 選項，例如要包含或排除特定函式的選項。 如需有關 VSInstr 選項的詳細資訊，請參閱 [VSInstr](../profiling/vsinstr.md)|- [如何：指定其他檢測選項](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>另請參閱

[設定效能會話](../profiling/configuring-performance-sessions.md) 
[如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md) 
[效能會話屬性](../profiling/performance-session-properties.md)
