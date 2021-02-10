---
title: 延伸標記 | Microsoft Docs
description: 瞭解範圍標記如何代表有意義的應用程式階段，並查看在並行視覺化中顯示範圍的範例。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 526d82194a4ed1463c802296cb97c95e0eb41d33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960139"
---
# <a name="span-markers"></a>延伸標記
延伸標記表示有意義的應用程式階段。 例如，您可以使用延伸範圍，表示其間正在處理特定工作項目的時間間隔。 其長度代表對應的應用程式階段持續時間。 下圖顯示並行視覺化檢視中的延伸範圍︰

 ![並行視覺化中的範圍標記](../profiling/media/cvmarkerspan.png ">cvmarkerspan") 並行視覺化中的範圍標記

## <a name="span-category"></a>延伸分類
 延伸標記共有五種不同的色彩，依其分類以其中一種顯示。 如果有五種以上的類別，則會重複這些色彩。 分類可以是任何整數。 下圖顯示五種可能的色彩︰

 ![不同類別的五個範圍](../profiling/media/cvmarkerspancategory.png ">cvmarkerspancategory") 前五個範圍類別的色彩

## <a name="span-aggregation-markers"></a>延伸彙總標記
 有時延伸標記發生的位置太靠近並行視覺化檢視中的另一個標記，以至於無法個別繪製。 發生這種情況時，會顯示一個表示基礎延伸範圍的灰色「延伸彙總標記」。 當您將指標放在這些圖示的其中一個時，工具提示會顯示所代表基礎延伸範圍的數目。 若要檢視延伸範圍，請予以放大。 如果您縮放到最大後仍然出現延伸彙總標記，您可以在[標記報告](../profiling/markers-report.md)中檢視基礎延伸標記。 下圖顯示延伸彙總標記︰

 ![並行視覺化中的匯總範圍標記](../profiling/media/cvmarkerspanaggregate.png ">cvmarkerspanaggregate") 範圍匯總標記

## <a name="see-also"></a>另請參閱
- [並行視覺化標記](../profiling/concurrency-visualizer-markers.md)
- [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)