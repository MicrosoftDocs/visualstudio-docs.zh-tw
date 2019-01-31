---
title: 資源監視效能規則 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09c9e41061564a8ffb0e08e3aba75a0d4355d0d2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795391"
---
# <a name="resource-monitoring-performance-rules"></a>資源監視效能規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[資源監視] 分類中的效能訊息提供應用程式效能的其他資料。 您可以使用這項資料來分析效能問題。 這些規則是參考性的，並針對每個分析回合進行報告。  
  
|||  
|-|-|  
|[DA0501：所分析之處理序的平均 CPU 消耗](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|此訊息報告處理器忙於執行應用程式指令的時間百分比。 報告的值是所分析的處理序作用中之所有測量間隔的平均。|  
|[DA0502：所分析之處理序的最大 CPU 消耗](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|此訊息報告處理器忙於執行應用程式指令的最大時間百分比。 報告的值是在所分析的處理序作用中之所有測量間隔當中報告的最大值。|  
|[DA0503：所分析的處理序的平均工作集 (以位元組為單位)](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|此訊息會報告處理序在分析作用時使用的平均實體記憶體數量 (以位元組為單位)。 此實體記憶體量值稱為工作集。|  
|[DA0504：所分析的處理序的最大工作集 (以位元組為單位)](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|此訊息會報告處理序在分析作用時使用的最大實體記憶體數量 (以位元組為單位)。|  
|[DA0505：為所分析的處理序配置的平均私用位元組](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|此訊息會報告處理序在分析作用時配置的平均虛擬記憶體數量 (以位元組為單位)。 此虛擬記憶體量值稱為「私用位元組」。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。|  
|[DA0506：為所分析的處理序配置的最大私用位元組](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|此訊息會報告處理序在分析作用時配置的最大虛擬記憶體數量 (以私用位元組 為單位)。|
