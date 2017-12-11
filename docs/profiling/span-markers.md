---
title: "延伸標記 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74919ddaa31bc7857a7bb9c30264830757f336b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="span-markers"></a>延伸標記
延伸標記表示有意義的應用程式階段。 例如，您可以使用延伸範圍，表示其間正在處理特定工作項目的時間間隔。 其長度代表對應的應用程式階段持續時間。 下圖顯示並行視覺化檢視中的延伸範圍︰  
  
 ![並行視覺化檢視中的延伸標記](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
並行視覺化檢視中的延伸標記  
  
## <a name="span-category"></a>延伸分類  
 延伸標記共有五種不同的色彩，依其分類以其中一種顯示。 如果有五種以上的類別，則會重複這些色彩。 分類可以是任何整數。 下圖顯示五種可能的色彩︰  
  
 ![五個不同分類的延伸標記](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
前五個延伸分類中的色彩  
  
## <a name="span-aggregation-markers"></a>延伸彙總標記  
 有時延伸標記發生的位置太靠近並行視覺化檢視中的另一個標記，以至於無法個別繪製。 發生這種情況時，會顯示一個表示基礎延伸範圍的灰色「延伸彙總標記」。 當您將指標放在這些圖示的其中一個時，工具提示會顯示所代表基礎延伸範圍的數目。 若要檢視延伸範圍，請予以放大。 如果您縮放到最大後仍然出現延伸彙總標記，您可以在[標記報告](../profiling/markers-report.md)中檢視基礎延伸標記。 下圖顯示延伸彙總標記︰  
  
 ![並行視覺化檢視中的彙總延伸標記](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
延伸彙總標記  
  
## <a name="see-also"></a>另請參閱  
 [並行視覺化檢視標記](../profiling/concurrency-visualizer-markers.md)   
 [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)