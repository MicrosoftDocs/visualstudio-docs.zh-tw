---
title: 效能規則參考 | Microsoft Docs
description: 瞭解分析工具的效能規則如何提供應用程式效能的其他警告和相關資訊。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ca20a6a1ad687fde432d0b748aa8b87c823a1da2
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723279"
---
# <a name="performance-rules-reference"></a>效能規則參考
程式碼剖析工具的效能規則提供關於應用程式效能的額外警告和資訊。 效能規則會分析從 Windows 和處理器效能計數器等來源收集到的程式碼剖析執行資料。 規則訊息會出現在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 整合式開發環境的 [錯誤輸出] 視窗。 訊息會隨下列其中一項規則層級同時列出：

|類別|描述|
|-|-|
|**錯誤**|一些規則產生錯誤訊息的原因，是因為大部分的效能問題不是徹底的錯誤。 錯誤訊息可能代表無法收集程式碼剖析資料。|
|**警告**|警告代表您應用程式的某個區域可能是效能問題的源頭，或該區域可能會因為最佳化而受益。|
|**資訊**|資訊訊息代表規則條件的分析未到達產生錯誤訊息的臨界值，或是訊息中的資訊有用，但無法反映效能問題。|

## <a name="in-this-section"></a>本節內容

[依識別碼的效能規則](../profiling/performance-rules-by-id.md)

程式碼剖析工具效能規則分成四個類別︰

|類別|描述|
|-|-|
|[.NET Framework 使用效能規則](../profiling/dotnet-framework-usage-performance-rules.md)|可協助您有效地使用 .NET Framework 的規則。|
|[記憶體和分頁效能規則](../profiling/memory-and-paging-performance-rules.md)|分析 Managed 記憶體和應用程式分頁行為的規則。|
|[分析工具使用規則](../profiling/profiling-tools-usage-rules.md)|可協助您有效地使用程式碼剖析工具的規則。|
|[資源監視效能規則](../profiling/resource-monitoring-performance-rules.md)|程式碼剖析執行中的處理器和記憶體使用率相關的資訊訊息。|
