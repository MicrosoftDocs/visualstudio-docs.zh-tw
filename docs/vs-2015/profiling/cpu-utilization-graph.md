---
title: CPU 使用率圖形 | Microsoft Docs
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
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: defa2f16a18c97a10f74e8d351152442ccc0907f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489071"
---
# <a name="cpu-utilization-graph"></a>CPU 使用率圖形
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CPU 使用率圖形](https://docs.microsoft.com/visualstudio/profiling/cpu-utilization-graph)。  
  
CPU 使用率圖形顯示應用程式經過一段時間的使用率等級。 X 軸代表追蹤的持續時間，而 y 軸代表系統上的邏輯核心數目。 圖形不會顯示在任何指定時間作用中的特定核心。 例如，如果兩個核心在某個指定期間各以 50% 的產能執行，則此檢視會顯示共使用一個邏輯核心。  
  
## <a name="cpu-utilization-graph-colors"></a>CPU 使用率圖形色彩  
  
-   綠色表示系統中目前處理序的邏輯核心使用率。  
  
-   淺灰色表示系統中其他處理序的邏輯核心使用率。 CPU 圖形中高百分比的淺灰色表示系統因為其他處理序而負載過重，而且您的處理序很可能會被它們先佔。 若要減少其他處理序的邏輯核心耗用量，請減少系統上執行的其他處理序數目。  
  
-   深灰色表示系統處理序的邏輯核心耗用量。 您無法直接控制這個值，但可以知道發生的時間，因為這會影響您的處理序是否能使用邏輯核心。  
  
-   白色表示系統上未使用的邏輯核心可用性。 如果您可以找到更多平行處理的機會，您的處理序就可以使用這些核心。  
  
## <a name="see-also"></a>另請參閱  
 [使用率檢視](../profiling/utilization-view.md)   
 [平均 CPU 使用率](../profiling/average-cpu-utilization.md)



