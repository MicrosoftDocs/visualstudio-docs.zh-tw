---
title: 使用 code map 分析器尋找潛在問題 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b15a6d95e2a64aa09d57cb4fba02ab0369be5799
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486283"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>使用 Code Map 分析器尋找潛在問題
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[尋找潛在的問題，使用程式碼對應分析器](https://docs.microsoft.com/visualstudio/modeling/find-potential-problems-using-code-map-analyzers)。  
  
在 Code Map 上執行分析器，以協助您識別可能過度複雜或需要改進的程式碼。 例如，您可以使用這些分析器：  
  
|**尋找具有下列項目的程式碼：**|**檢查這些區域，以查看是否**|  
|-------------------------------|--------------------------------------------|  
|迴圈或循環相依性|您可以將其簡化，並考慮是否可以中斷這些循環。|  
|太多相依性|相依性正在執行太多函式，或者將決定變更這些區域的影響。 格式正確的 Code Map 會顯示最少的相依性。 若要讓程式碼更容易維護、變更、測試和重複使用，請考慮是否重構這些區域，以便能更清楚地加以定義，或考慮是否合併執行類似功能的程式碼。|  
|沒有任何相依性|它們是必要的，或者您是否應移除此程式碼。|  
  
## <a name="analyze-code-maps"></a>分析 Code Map  
  
1.  在對應工具列上選擇 [配置] 、[分析器] 以及您想要執行的分析器：  
  
    |**分析器**|**若要識別具有下列項目的節點：**|  
    |------------------|--------------------------------|  
    |**循環參考分析器**|對彼此具有循環的相依性。 **注意︰** 循環相依性中**泛型**時展開的群組群組不會在地圖上顯示。|  
    |**尋找中樞分析器**|為前 25% 的高度連接節點<br /><br /> **隱藏對應上的所有其他節點**<br /><br /> -開啟對應的捷徑功能表，選擇 **進階**，**選取**，**隱藏未選取**。<br />     對應會隱藏未選取的節點，且分析器將識別作為中樞的新節點。|  
    |**未參考的節點分析器**|不具有來自其他任何節點的參考。 **注意：** 確認之前所有這些情況下，假設不使用程式碼。 在程式碼中，找不到像是 XAML 相依性和執行階段相依性這樣的靜態特定相依性。|  
  
 在您套用之後，Code Map 分析器將繼續執行。 如果您變更對應，所套用的任何分析器將自動重新處理已更新的對應。 若要停止執行分析器，在對應工具列上選擇 [配置] ，然後選擇[分析器] 。 關閉所選的分析器。  
  
> [!TIP]
>  如果您的對應非常大，執行分析器可能會造成記憶體不足的例外狀況。 如果發生這種情況，請編輯對應以減少其範圍，或產生較小的對應，然後執行分析器。  
  
## <a name="see-also"></a>另請參閱  
 [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)   
 [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)   
 [在偵錯時於呼叫堆疊上對應方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)



