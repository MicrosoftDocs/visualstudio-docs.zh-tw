---
title: "使用率導覽 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c68443f15330a63e8372445fcbd80be8bd0dfc18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="utilization-navigator"></a>使用率導覽
您可以使用並行視覺化檢視中的使用率導覽，選取追蹤中的一段時間。 並行視覺化檢視會顯示目標處理序在一段時間內的 CPU 核心使用率。 這可讓您更輕鬆地檢查 CPU 使用率模式，也可讓您比較使用率資料與其他檢視中的資料。 使用率導覽會出現在並行視覺化檢視中的每個檢視頂端。 下圖顯示使用率導覽。  
  
 ![顯示所選時間範圍的使用率導覽](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
使用率導覽和所選時間範圍  
  
 在圖中，以紅色矩形定義的選取間隔，稱為 thumb。  
  
 以下是您可以用使用率導覽來顯示時間範圍的操控方式：  
  
-   您可以左右拖曳 Thumb 來移動瀏覽。 (鍵盤︰將焦點移至 thumb，然後按向左鍵或向右鍵。)  
  
-   您可以拖曳其中一個控點來變更間隔的範圍。 (鍵盤︰將焦點移至控點，然後按向右鍵或向左鍵。)  
  
 如果您使用不同的並行視覺化檢視縮放控制項來變更間隔，使用率導覽會更新以反映變更。