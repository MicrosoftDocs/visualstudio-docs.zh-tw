---
title: GPU 活動圖 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c274bc5c98a856e5d2f921f2967d8ee474f06274
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833309"
---
# <a name="gpu-activity-graph"></a>GPU 活動圖
並行視覺化檢視中的 GPU 活動圖顯示系統上的 DirectX 活動層級，這是以一段時間內使用中的 DirectX 引擎數目來測量。  活動圖不會顯示使用哪些特定引擎。  正在處理任一 GPU 工作的引擎會視為使用中。  
  
## <a name="gpu-activity-graph-colors"></a>GPU 活動圖色彩  
 綠色表示目前處理序的 DirectX 引擎的耗用量。  
  
 淺灰色表示系統上其他處理序的 DirectX 引擎耗用量。 若要減少其他處理序的 DirectX 引擎耗用量，請減少系統上執行的其他處理序數目。  
  
 白色表示系統上未使用的 DirectX 引擎的可用性。 如果您可以找到更多機會利用它們，這些引擎都適用於您的處理序。 部分引擎只能用於特定種類的工作。  
  
## <a name="see-also"></a>另請參閱  
 [使用率檢視](../profiling/utilization-view.md)