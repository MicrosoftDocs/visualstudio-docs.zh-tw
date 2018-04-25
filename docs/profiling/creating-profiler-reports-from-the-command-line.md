---
title: 從命令列建立分析工具報表 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c7bde83ce810f8260e61eacddf1a086953a63a4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="creating-profiler-reports-from-the-command-line"></a>從命令列建立程式碼剖析工具報告
**VSPerfReport** 命令列工具可讓您從分析資料 (.vsp) 檔案建立.xml 或以逗號分隔值 (.csv) 報表。 VSPerfReport 報表類型極符合 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之介面的資料表檢視。 您可以篩選報表只顯示您的程式碼，以及只顯示分析資料檔案的區段。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
 您也可以更輕鬆地共用分析資料檔案，方法是將符號內嵌到 .vsp 檔案，以及建立較小且更快速開啟的預先分析報表 (.vsps) 檔案。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**建立基本報表。** 建立所有 VSPerfReport 報表類型或其子集。|-   [建立基本報表](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**比較兩個分析資料檔案。** 建立 "diff" 報表，以比較兩個分析資料檔案中的效能資料。|-   [如何：從命令提示字元建立分析工具比較報表](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**檢視呼叫追蹤和 Windows 事件追蹤 (ETW) 資料。** 建立呼叫追蹤報表，以列出您應用程式函式每個進入點和結束點的計時資訊，以及您的函式對其他函式的每次呼叫。 或者，建立分析回合中所收集之所有 ETW 事件的詳細清單。|-   [如何：建立呼叫追蹤報表](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**篩選報表。** 限制報表，只顯示程式碼中的函式或分析資料檔案中的特定時間。|-   [如何：從命令列篩選報表](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**建立可移植的分析資料檔案。** 若要更輕鬆地共用分析資料，您可以將分析回合的符號內嵌到 .vsp 檔案。 您也可以建立較小且更快速開啟之預先分析的分析資料 (.vsps) 檔案。|-   [建立可移植的分析資料檔案](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|