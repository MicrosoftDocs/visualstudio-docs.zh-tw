---
title: "活動檢視 （舊版） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 50f57684db32f601bd4cbf870456da458aa5ce7c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="activity-views-legacy"></a>活動檢視 (舊版)
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 提供的許多活動 (工作流程組成的元素) 具有舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中所提供的幾個設計檢視。 當您拖曳的活動設計工具**工具箱**拖曳至設計介面，以及此後每次選取活動時，您可以在使用不同的設計檢視之間切換**工作流程**功能表或以滑鼠右鍵按一下選取的活動。 此外，當您將指標移至選取活動的名稱上方時，會顯示一組下拉式索引標籤，可用來在不同的檢視之間切換。  
  
 每個活動有至少一個檢視。這是顯示當您拖曳的活動設計工具的預設檢視**工具箱**拖曳至設計介面。 此活動預設檢視中可做為**檢視 [活動類型]**選項功能表和索引標籤上，例如**檢視 Parallel**。 大部分的活動會有額外的檢視，不同的活動可以有不同的檢視。 例如， [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)活動有補償檢閱和[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)活動有事件檢視。 許多隨附於 Windows Workflow Foundation 活動都有**檢視取消處理常式**和**檢視錯誤**設計檢視來檢視[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)和[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與其相關聯。  
  
 下表列出每個檢視的名稱和說明。  
  
|功能表/索引標籤選項|說明|  
|----------------------|-----------------|  
|**檢視 [活動類型]**|選取此功能表或索引標籤選項可檢視所選活動的預設圖形表示。|  
|**檢視取消處理常式**|選取此功能表或索引標籤選項可檢視[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)與所選活動相關聯。|  
|**檢視錯誤處理常式**|選取此功能表或索引標籤選項可檢視[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與所選活動相關聯。|  
|**檢視補償處理常式**|選取此功能表或索引標籤選項可檢視[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)選取相關聯[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)。|  
|**檢視事件處理常式**|選取此功能表或索引標籤選項可檢視[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)選取相關聯[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)。|  
  
 類似的檢視表的相關資訊，請參閱[循序工作流程檢視 （舊版）](../workflow-designer/sequential-workflow-views-legacy.md)。  
  
## <a name="see-also"></a>另請參閱  
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [循序工作流程檢視 (舊版)](../workflow-designer/sequential-workflow-views-legacy.md)