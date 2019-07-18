---
title: 活動檢視 （舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62b3c9185226512ff28c8d028cd0ba7d33b0f12f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977445"
---
# <a name="activity-views-legacy"></a>活動檢視 (舊版)
[!INCLUDE[wf](../includes/wf-md.md)] 提供的許多活動 (工作流程組成的元素) 具有舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中所提供的幾個設計檢視。 當您拖曳的活動設計工具**工具箱**拖曳至設計介面，之後每當您選取活動時，您可以在使用其中一種在不同的設計檢視之間切換**工作流程**功能表或以滑鼠右鍵按一下選取的活動。 此外，當您將指標移至選取活動的名稱上方時，會顯示一組下拉式索引標籤，可用來在不同的檢視之間切換。  
  
 每個活動都有至少一個檢視;這是顯示當您拖曳的活動設計工具的預設檢視**工具箱**拖曳至設計介面。 此活動的預設檢視是可**檢視 [活動類型]** 選項的功能表和索引標籤上，例如**檢視 Parallel**。 大部分的活動會有額外的檢視，不同的活動可以有不同的檢視。 例如， [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)活動有補償檢閱並[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)活動有事件檢視。 許多 Windows Workflow Foundation 所隨附的活動都有**檢視取消處理常式**並**檢視錯誤**設計檢視，可檢視[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)並[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與其相關聯。  
  
 下表列出每個檢視的名稱和說明。  
  
|功能表/索引標籤選項|描述|  
|----------------------|-----------------|  
|**檢視 [活動類型]**|選取此功能表或索引標籤選項可檢視所選活動的預設圖形表示。|  
|**檢視取消處理常式**|選取此功能表或索引標籤的選項可檢視[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)與所選活動相關聯。|  
|**檢視錯誤處理常式**|選取此功能表或索引標籤的選項可檢視[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與所選活動相關聯。|  
|**檢視補償處理常式**|選取此功能表或索引標籤的選項可檢視[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)與 選取相關聯[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)。|  
|**檢視事件處理常式**|選取此功能表或索引標籤的選項可檢視[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)與 選取相關聯[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)。|  
  
 如需類似檢視的詳細資訊，請參閱[循序工作流程檢視 （舊版）](../workflow-designer/sequential-workflow-views-legacy.md)。  
  
## <a name="see-also"></a>另請參閱  
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [循序工作流程檢視 (舊版)](../workflow-designer/sequential-workflow-views-legacy.md)