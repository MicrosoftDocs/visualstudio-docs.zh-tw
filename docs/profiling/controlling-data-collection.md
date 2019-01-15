---
title: 控制資料收集 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89c1f0b435790622bee54b6cf91d57bd0cc9be29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848781"
---
# <a name="control-data-collection"></a>控制資料收集
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具可讓您控制在效能工作階段期間收集分析資料的時間，並指定分析的函式。 本節說明如何從 [效能總管] 和 [資料收集控制] 視窗啟動和停止資料收集，以及如何限制要收集其分析資料的物件。  
  
## <a name="common-tasks"></a>一般工作
  
|工作|相關內容|  
|----------|---------------------|  
|**啟動和停止分析：** 您可以在應用程式啟動時開始分析應用程式，也可以將分析工具附加至已經在執行中的處理序。 當目標應用程式執行時，您可以暫停和繼續收集資料。 您可以關閉目標應用程式，或將分析工具與執行中的處理序中斷連結，來結束分析工作階段。|-   [如何：開始和結束效能資料收集](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [如何：為執行中的處理序附加和中斷連結效能工具](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [如何：暫停和繼續效能資料收集](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**設定檢測分析以限制收集的資料：** 您可以使用效能工作階段組態屬性來限制在執行分析時使用檢測方法收集的資料。 您可以包含或排除特定的 .dll 檔案、命名空間、類別和函式。 您也可以排除不符合您指定之大小閾值的函式。|-   [如何：限制檢測特定 DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [如何：從檢測排除或包含精簡函式](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>相關章節  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>另請參閱  
 [效能總管](../profiling/performance-explorer.md)