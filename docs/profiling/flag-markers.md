---
title: 旗標標記 | Microsoft Docs
description: 深入瞭解旗標標記會在 Visual Studio 平行存取視覺化檢視中進行。 旗標標記表示在應用程式時間中的某個時刻發生的項目。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc7b128915b7fc961b44aa7d70a24a813d432ddf
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801468"
---
# <a name="flag-markers"></a>旗標標記
旗標標記表示在應用程式時間中的某個時刻發生的項目。 旗標可代表許多種類的應用程式事件。 比方說，當特定工作項目已排程或擲回例外狀況時，可以顯示旗標。 工作平行程式庫等的執行階段也可以產生旗標。

## <a name="flag-importance"></a>旗標重要性
 旗標會依其重要性以不同的大小顯示。 與所有標記一樣，重要性可以是低、普通、高或嚴重。  下圖顯示標記的外觀 (依重要性層級排列)︰

 ![低、普通、高和重大重要性標記](../profiling/media/cvmarkerimportance.png ">cvmarkerimportance") 顯示旗標重要性的標記

## <a name="flag-category"></a>旗標分類
 旗標共有五種不同的色彩，依其分類以其中一種顯示。 如果有五種以上的類別，則會重複使用這些色彩。 您無法選擇色彩。 與所有標記一樣，分類可以是任何整數。 下圖顯示前五個類別的色彩。

 ![五種分類標記色彩](../profiling/media/cvmarkercategory.png ">cvmarkercategory") 顯示類別的標記

## <a name="alerts"></a>警示
 警示為紅色旗標，表示嚴重的應用程式事件，例如例外狀況。  以下是警示︰

 ![平行存取視覺化警示標記](../profiling/media/cvmarkeralert.png ">cvmarkeralert") 警示標記

## <a name="aggregation-flags"></a>彙總旗標
 有時旗標發生的位置太靠近並行視覺化檢視中的另一個旗標，以至於無法個別繪製。 發生這種情況時，會顯示一個表示基礎旗標的灰色 *彙總旗標*。 當您將指標放在這些圖示的其中一個時，工具提示會顯示所代表基礎旗標的數目。 若要檢視旗標，請將它放大。 如果您縮放到最大後仍然出現彙總旗標，可以在[標記報表](../profiling/markers-report.md)中檢視基礎旗標。

 彙總旗標以不同大小繪製。 大小取決於最重要的旗標在彙總中的重要性層級。 下圖顯示以遞增的重要性順序排序的彙總旗標。

 ![顯示四個重要性層級的匯總旗標](../profiling/media/cvmarkeraggregate.png ">cvmarkeraggregate") 依重要性層級的匯總旗標

## <a name="see-also"></a>另請參閱
- [並行視覺化標記](../profiling/concurrency-visualizer-markers.md)
- [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)