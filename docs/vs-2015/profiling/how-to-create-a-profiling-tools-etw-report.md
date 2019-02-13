---
title: 如何：建立分析工具 ETW 報告 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e8ad32f3231915c86f9578563ec4c0684435a3ee
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797333"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>如何：建立程式碼剖析工具 ETW 報告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「Windows 事件追蹤」(ETW) 報告會列出「[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具」的效能工作階段中記錄的 ETW 事件。 ETW 資料會收集在二進位 (.etl) 檔案中。 如需有關此報告的詳細資訊，請參閱 [Windows 事件追蹤 (ETW) 報告](../profiling/event-tracing-for-windows-etw-report.md)。  
  
> [!NOTE]
>  您無法在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的介面中顯示 ETW 報告。  
  
- 如需有關如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的介面來收集 ETW 資料的資訊，請參閱[如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)。  
  
- 如需有關如何從命令提示字元收集 ETW 資料的資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 和 [Events](../profiling/events-vsperfcmd.md)。  
  
  您可以使用 **VSReport/summary:etw** 命令來產生 ETW 報告。 包含 ETW 資料的 .etl 必須位於與分析資料檔 (.vsp 或 .vsps) 相同的目錄中。 根據預設，產生報告時，會以逗號分隔值 (.csv) 檔案的形式產生。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
### <a name="to-generate-an-etw-report"></a>產生 ETW 報告  
  
-   在 [命令提示字元] 視窗中，輸入下列命令行：  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|「分析工具」公用程式的路徑。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。|  
    |*VSPFile*|分析資料檔 (.vsp 或 .vsps)。 可接受完整和部分路徑。|  
    |Xml|產生採用 XML 格式的報告。|
