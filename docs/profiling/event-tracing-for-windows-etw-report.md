---
title: Windows 事件追蹤 (ETW) 報表 | Microsoft Docs
description: 閱讀 Windows 事件追蹤 (ETW) 報告，其中列出 Visual Studio 分析工具的效能會話中記錄的 ETW 事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e7167f2fb5c78a6fa8c3d83fb56c2c2eba217516
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801420"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows 事件追蹤 (ETW) 報表
Windows 事件追蹤 (ETW) 報表會列出 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具之效能工作階段中所記錄的 ETW 事件。 ETW 資料會收集在二進位 (.*etl*) 檔案中。

> [!NOTE]
> 您無法在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 介面中顯示 ETW 報表。

- 如需如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 介面中的分析工具來收集 ETW 的資訊，請參閱[如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)。

- 如需如何使用 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具收集 ETW 資料的資訊，請參閱[資料](../profiling/events-vsperfcmd.md)。

- 您可以使用 **>vsreport/Summary： etw** 命令來產生 etw 報告。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。

|資料行|描述|
|------------|-----------------|
|**Timestamp**|識別事件發生的時間。|
|**處理序識別碼**|識別已產生事件的處理序。|
|**執行緒識別碼**|識別已產生事件的執行緒。|
|**說明**|識別事件提供者。|
|**型別**|識別事件類型。|
|**屬性**|事件的屬性。 每個事件都是以中括弧括住的名稱/值組 (以逗點分隔)。|
