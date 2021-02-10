---
title: 使用取樣收集效能統計資料
description: 流量分析工具取樣方法來尋找處理器使用量問題。 這是開始進行大部分效能調查的建議方法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b04d6ab450d933c75190af9baa9ec6f41549bd82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950217"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>使用取樣收集效能統計資料

根據預設，Visual Studio 分析工具取樣方法會每 10,000,000 個處理器循環 (在 1 GHz 電腦上大約是每隔百分之一秒) 即收集一次分析資訊。 取樣方法可用來尋找處理器使用率的問題，建議用來調查大多數效能問題。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

您可以使用下列其中一種程序來指定取樣方法：

- 在分析精靈的第一個頁面上，按一下 [CPU 取樣 (建議使用)]。
- 在 [效能總管] 工具列的 [方法] 清單中，按一下 [取樣]。
- 在效能工作階段 [屬性] 對話方塊中的 [一般] 頁面上，按一下 [取樣]。

## <a name="common-tasks"></a>常見工作

您可以在效能會話的 [_效能會話_]**屬性頁** 對話方塊中指定其他選項。 若要開啟此對話方塊：

- 在 **效能總管** 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 [屬性] 。

  下表中的工作說明當您使用取樣方法進行分析時，可以在 [效能工作階段屬性頁] 對話方塊中指定的選項。

|Task|相關內容|
|----------|---------------------|
|在 [一般] 頁面，加入 .NET 記憶體配置和存留期資料的收集，並指定產生的分析資料 (.vsp) 檔案的命名詳細資料。|- [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|
|在 [取樣] 頁面上，變更取樣率、將取樣事件從處理器時脈循環變更為另一個處理器效能計數器，或變更這兩者...|- [如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)|
|在 [啟動] 頁面上，如果您的程式碼方案中有多個 .exe 專案，請指定要啟動的應用程式和啟動順序。|- [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|
|在 [階層 **互動** ] 頁面上，將 ADO.NET 呼叫資訊新增至分析執行中所收集的資料。|- [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|
|在 [Windows 事件] 頁面上，指定一或多個要收集取樣資料的 Windows 事件追蹤 (ETW) 事件。|- [如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|在 [Windows 計數器]  頁面上，指定將加入程式碼剖析資料為標記的一或多個作業系統效能計數器。|- [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|
|在 [進階] 頁面上，如果您的應用程式模組使用多個版本，請指定要分析的 .NET Framework 執行階段版本。 預設會分析載入的第一個版本。|- [如何：指定 .NET Framework 執行時間](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
