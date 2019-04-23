---
title: Windows 事件追蹤 (ETW) 報表 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bfcb10bdbbfcb8e4b98f8d90d6652832059107d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108213"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows 事件追蹤 (ETW) 報告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 事件追蹤 (ETW) 報表會列出 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具之效能工作階段中所記錄的 ETW 事件。 ETW 資料會收集在二進位 (.etl) 檔案中。  
  
> [!NOTE]
>  您無法在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 介面中顯示 ETW 報表。  
  
- 如需如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 介面中的分析工具來收集 ETW 的資訊，請參閱[如何：Windows (ETW) 資料收集事件追蹤](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)。  
  
- 如需如何使用 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具收集 ETW 資料的資訊，請參閱[資料](../profiling/events-vsperfcmd.md)。  
  
- 您可以使用 **VSReport/Summary:ETW** 命令來產生 ETW 報表。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
|資料行|描述|  
|------------|-----------------|  
|**時間戳記**|識別事件發生的時間。|  
|**處理序 ID**|識別已產生事件的處理序。|  
|**執行緒 ID**|識別已產生事件的執行緒。|  
|**描述**|識別事件提供者。|  
|**Type**|識別事件類型。|  
|**屬性**|事件的屬性。 每個事件都是以中括弧括住的名稱/值組 (以逗點分隔)。|
