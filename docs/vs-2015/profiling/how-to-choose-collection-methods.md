---
title: 如何：選擇收集方法 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aaa4c13509d02deacd719a52c2ac6514d4c0827
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485965"
---
# <a name="how-to-choose-collection-methods"></a>如何：選擇收集方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 選擇收集方法](https://docs.microsoft.com/visualstudio/profiling/how-to-choose-collection-methods)。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具支援三種效能資料收集方法︰取樣、檢測和並行。 您也可以使用取樣或檢測方法來收集 .NET 記憶體配置和存留期資料。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 您可以使用效能工作階段 **Method** 屬性來指定最適合您的應用程式的收集方法。 您可以從 [效能精靈]、[效能總管] 或效能工作階段中的屬性頁面設定收集方法。 如果您使用命令列工具，請參閱[從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)以了解詳細資訊。  
  
## <a name="performance-wizard"></a>效能精靈  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>使用 [效能精靈] 選取收集方法  
  
-   在精靈的第一個頁面上，選取下列其中一個選項︰  
  
|選項|描述|  
|------------|-----------------|  
|**CPU 取樣**|收集對初始分析和 CPU 使用率問題分析有用的應用程式統計資料。|  
|**檢測**|收集對重點分析和輸入/輸出效能問題分析有用的詳細計時資料。|  
|**.NET 記憶體配置**|使用取樣分析方法收集 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 記憶體配置資料。|  
|**並行**|收集數值資源爭用資料。|  
  
## <a name="performance-explorer"></a>效能總管  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>使用 [效能總管] 選取收集方法  
  
1.  在 [效能總管] 工具列上，按一下 [方法] 下拉式清單旁的箭號。  
  
2.  按一下您偏好的收集方法。  
  
## <a name="performance-session-property-pages"></a>效能工作階段屬性頁  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>使用效能工作階段屬性選取取樣或檢測方法  
  
1.  在 [效能總管] 中，選取效能工作階段。  
  
     效能工作階段檔案名稱的副檔名為 .psess。  
  
2.  以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性]。  
  
3.  在 [屬性頁] 中，按一下 [一般] 頁面。  
  
4.  按一下您偏好的收集方法。  
  
    -   如需收集取樣資料時可用的其他選項的詳細資訊，請參閱[使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)。  
  
    -   如需收集取樣資料時可用的其他選項的詳細資訊，請參閱[使用檢測收集計時詳細資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)。  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>使用效能工作階段屬性選取 .NET 記憶體資料收集  
  
1.  在 [效能總管] 中，選取效能工作階段。  
  
     效能工作階段檔案名稱的副檔名為 .psess。  
  
2.  以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性]。  
  
3.  在 [屬性頁] 中，按一下 [一般] 頁面。  
  
4.  按一下 [取樣] 或 [檢測]。  
  
5.  按一下 [收集 .NET 物件配置資訊] 以收集 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 物件配置的大小和數目。  
  
6.  (選擇性) 按一下 [同時收集 .NET 物件存留期的資訊]，以收集回收物件記憶體的記憶體回收層代相關資料。  
  
     如需收集 .NET 記憶體資料時可用的其他選項的詳細資訊，請參閱[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)。  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>使用效能工作階段屬性選取並行資料收集  
  
1.  在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。  
  
2.  在 [屬性頁] 中，按一下 [一般] 頁面。  
  
3.  按一下 [並行]。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)



