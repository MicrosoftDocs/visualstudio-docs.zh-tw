---
title: 如何：建立分析工具 ETW 報告 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a49ab3f00eb74edb3be3f733b3c0d70f8613d862
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>如何：建立程式碼剖析工具 ETW 報告
「Windows 事件追蹤」(ETW) 報告會列出「[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具」的效能工作階段中記錄的 ETW 事件。 ETW 資料會收集在二進位 (.etl) 檔案中。 如需有關此報告的詳細資訊，請參閱 [Windows 事件追蹤 (ETW) 報告](../profiling/event-tracing-for-windows-etw-report.md)。  
  
> [!NOTE]
>  您無法在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中顯示 ETW 報告。  
  
-   如需有關如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面來收集 ETW 資料的資訊，請參閱[如何：收集 Windows 事件追蹤 (ETW) 資料](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)。  
  
-   如需有關如何從命令提示字元收集 ETW 資料的資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 和 [Events](../profiling/events-vsperfcmd.md)。  
  
 您可以使用 **VSReport/summary:etw** 命令來產生 ETW 報告。 包含 ETW 資料的 .etl 必須位於與分析資料檔 (.vsp 或 .vsps) 相同的目錄中。 根據預設，產生報告時，會以逗號分隔值 (.csv) 檔案的形式產生。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
### <a name="to-generate-an-etw-report"></a>產生 ETW 報告  
  
-   在 [命令提示字元] 視窗中，輸入下列命令行：  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|「分析工具」公用程式的路徑。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。|  
    |*VSPFile*|分析資料檔 (.vsp 或 .vsps)。 可接受完整和部分路徑。|  
    |Xml|產生採用 XML 格式的報告。|