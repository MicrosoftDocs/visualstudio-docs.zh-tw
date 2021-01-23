---
title: 使用率導覽 |Microsoft 文件
description: 瞭解如何使用並行視覺化視覺化中的使用率導覽，來選取追蹤中的時間間隔。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f209098200333e91f0e5baf9c7a2b73b4a3202f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723214"
---
# <a name="utilization-navigator"></a>使用率導覽
您可以使用並行視覺化檢視中的使用率導覽，選取追蹤中的一段時間。 並行視覺化檢視會顯示目標處理序在一段時間內的 CPU 核心使用率。 這可讓您更輕鬆地檢查 CPU 使用率模式，也可讓您比較使用率資料與其他檢視中的資料。 使用率導覽會出現在並行視覺化檢視中的每個檢視頂端。 下圖顯示使用率導覽。

 ![顯示所選時間範圍的使用率](../profiling/media/cvutilizationnavigator.png ">cvutilizationnavigator") 導覽使用率導覽和所選時間範圍

 在圖中，以紅色矩形定義的選取間隔，稱為 thumb。

 以下是您可以用使用率導覽來顯示時間範圍的操控方式：

- 您可以左右拖曳 Thumb 來移動瀏覽。 (鍵盤︰將焦點移至 thumb，然後按向左鍵或向右鍵。)

- 您可以拖曳其中一個控點來變更間隔的範圍。 (鍵盤︰將焦點移至控點，然後按向右鍵或向左鍵。)

  如果您使用不同的並行視覺化檢視縮放控制項來變更間隔，使用率導覽會更新以反映變更。