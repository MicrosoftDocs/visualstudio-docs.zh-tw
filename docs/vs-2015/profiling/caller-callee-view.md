---
title: 呼叫端-被呼叫端檢視 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 37
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a28f0184d126781c43540d447cd75cd905e15d40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487331"
---
# <a name="callercallee-view"></a>呼叫端/被呼叫端檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[呼叫端-被呼叫端檢視](https://docs.microsoft.com/visualstudio/profiling/caller-callee-view)。  
  
[呼叫端/被呼叫端] 檢視會顯示所選取函式及其父函式和子函式的分析資訊。 [呼叫端/被呼叫端] 檢視包含三個方格：  
  
 **目前的函式**會顯示在中間方格中，顯示所選取函式的分析資訊。 值包含在分析執行中所收集的所有函式呼叫。  
  
 **呼叫目前函式的函式**會顯示在上方方格中，顯示所選取 (目前) 函式 (從呼叫端 (父) 函式的呼叫所產生) 的值數目。  
  
 **目前的函式所呼叫的函式**會顯示在下方方格中，顯示所選取函式之被呼叫端 (子) 函式 (由目前函式所呼叫) 的分析資訊。  
  
 [呼叫端/被呼叫端] 檢視中可用的資料行取決於用來收集資料的分析方法 (取樣或檢測)，以及分析執行是否收集 .NET 記憶體資料。  
  
 您可以選取不同的函式，讓函式成為 [報表] 檢視中間[目前的函式]，只要連按兩下檢視其他兩個部分中所列出的其中一個函式即可。 [報表] 檢視會自動更新以反映變更。  
  
 您可以按一下資料行名稱來排序資料。 [呼叫端/被呼叫端] 檢視可以加入其他資料行。 如需詳細資訊，請參閱[如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫端/被呼叫端檢視 - 取樣資料](../profiling/caller-callee-view-sampling-data.md)   
 [呼叫端/被呼叫端檢視 - 檢測資料](../profiling/caller-callee-view-instrumentation-data.md)   
 [呼叫端/被呼叫端檢視 - .NET 記憶體檢測資料](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [呼叫端/被呼叫端檢視 - .NET 記憶體取樣資料](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [呼叫端/被呼叫端檢視 - 爭用資料](../profiling/caller-callee-view-contention-data.md)



