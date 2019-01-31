---
title: 核心檢視圖例 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05f768f6ff928ab00ebbd503c1ae9826dab8cd38
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780578"
---
# <a name="cores-view-legend"></a>核心檢視圖例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

核心檢視圖例依色彩和名稱識別每個執行緒。 當中包含顯示跨核心內容切換計數、內容切換總數，以及跨核心之內容切換百分比的欄。 圖例中的列以遞減順序，依跨核心內容切換的次數排序。  
  
 您可以選取圖例中的列篩選在時間軸中顯示的執行緒。 時間軸只會顯示選取的執行緒。 如果您不選取任何列，時間軸會顯示所有列。  
  
 跨核心內容切換比起保留在相同邏輯核心中的切換花費更多的負荷和效能。 在內容切換期間會儲存及還原處理器暫存器、執行作業系統核心程式碼、重新載入轉譯對應緩衝區項目，以及排清處理器管線。 跨核心內容切換可能比其他內容切換更加耗用資源，因為此執行緒的快取資料在另一個核心無效。 相反地，如果執行緒內容切換到先前執行的核心上，快取中很可能還是有有用的資料。 當跨核心內容切換已增加管理執行緒同質性的嘗試次數，且效能也降低時，請考慮是否要解決此問題。 請先消除執行緒同質性，然後觀察產生的跨核心行為。  
  
 下表描述圖例項目。  
  
|元素|定義|  
|-------------|----------------|  
|執行緒名稱|顯示前一個核心時間軸中執行緒的名稱和執行緒的色彩。|  
|跨核心內容切換|執行緒也從一個邏輯核心切換到另一個的內容切換次數。 它不會區分從一個處理器晶粒跨越到另一個的跨核心內容切換，與留在相同晶粒上的跨核心內容切換。|  
|總計內容切換次數|在取樣期間內指定執行緒的內容切換總數。 每次當執行緒變更內容 (例如，從執行到同步處理) 時，就計算一次內容切換。|  
|跨核心內容切換的百分比|以跨核心內容切換總數除以內容切換總數的百分比計算。 這個百分比越高，跨核心內容切換的負荷對於此特定執行緒的效能整體影響越大。|  
  
## <a name="see-also"></a>請參閱  
 [核心檢視](../profiling/cores-view.md)
