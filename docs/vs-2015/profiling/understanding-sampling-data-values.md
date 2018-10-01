---
title: 了解取樣資料值 | Microsoft Docs
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
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60087d2788cd4b46b77d670cf430bf0e0198b6f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490816"
---
# <a name="understanding-sampling-data-values"></a>認識取樣資料值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[了解取樣資料值](https://docs.microsoft.com/visualstudio/profiling/understanding-sampling-data-values)。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具的「取樣」分析方法會依設定的間隔來中斷電腦處理器，並收集函式呼叫堆疊。 「呼叫堆疊」是一個動態結構，其中儲存在處理器上執行的函式相關資訊。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 分析工具分析會判斷處理器是否正在執行目標處理序中的程式碼。 如果處理器未在執行目標處理序中的程式碼，則會捨棄此樣本。  
  
 如果處理器在執行目標程式碼，分析工具會讓呼叫堆疊上每個函式的樣本計數遞增。 取樣時，呼叫堆疊上只能有一個函式正在執行程式碼。 堆疊上的其他函式則是函式呼叫階層中的父代，會等候其子系傳回。  
  
 對於樣本事件，該分析工具會讓目前正在執行其指示的函式「專有」樣本計數遞增。 因為專有樣本也是函式總 (內含) 樣本數的一部分，所以目前作用中函式的內含樣本計數也會遞增。  
  
 分析工具會讓呼叫堆疊上所有其他函式的內含樣本計數遞增。  
  
## <a name="inclusive-samples"></a>內含樣本  
 目標函式執行期間所收集的樣本總數。  
  
 這包括在直接執行函式程式碼期間收集的樣本，以及在執行目標函式所呼叫子函式期間收集的樣本。  
  
## <a name="exclusive-samples"></a>專有樣本  
 目標函式直接執行指示期間所收集的樣本數。  
  
 專有樣本不包含目標函式所呼叫的函式執行期間所收集的樣本。  
  
## <a name="inclusive-percent"></a>內含百分比  
 就程式碼剖析執行時的內含樣本總數，函式或資料範圍的內含樣本所佔的百分比。  
  
## <a name="exclusive-percent"></a>專有百分比  
 就程式碼剖析執行時的專有樣本總數，函式或資料範圍的專有樣本所佔的百分比。  
  
## <a name="see-also"></a>另請參閱  
 [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)   
 [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)



