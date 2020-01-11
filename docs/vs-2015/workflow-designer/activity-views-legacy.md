---
title: 即時檢視（舊版） |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851472"
---
# <a name="activity-views-legacy"></a>活動檢視 (舊版)
[!INCLUDE[wf](../includes/wf-md.md)] 提供的許多活動 (工作流程組成的元素) 具有舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中所提供的幾個設計檢視。 當您將活動設計工具從 [**工具箱**] 拖曳至設計介面，並在每次選取活動時，您可以使用 [**工作流程**] 功能表或以滑鼠右鍵按一下選取的活動，在不同的設計檢視之間切換。 此外，當您將指標移至選取活動的名稱上方時，會顯示一組下拉式索引標籤，可用來在不同的檢視之間切換。

 每個活動至少有一個視圖;這是當您將活動設計工具從 [**工具箱**] 拖曳至設計介面時，所顯示的預設視圖。 這個活動的預設 view 在功能表和索引標籤上是以**view [activity type]** 選項的形式提供，例如， **view Parallel**。 大部分的活動會有額外的檢視，不同的活動可以有不同的檢視。 例如，[ [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) ] 活動具有 [補償] 視圖，而 [ [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) ] 活動具有 [事件] 視圖。 Windows Workflow Foundation 隨附的許多活動都具有**View Cancel Handler**和**view 錯誤**設計檢視，以查看[CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx)及其相關聯的[FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) 。

 下表列出每個檢視的名稱和說明。

|功能表/索引標籤選項|描述|
|----------------------|-----------------|
|**View [活動類型]**|選取此功能表或索引標籤選項可檢視所選活動的預設圖形表示。|
|**View 取消處理常式**|選取此功能表或 [索引標籤] 選項視圖，以查看與所選活動相關聯的[CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) 。|
|**查看錯誤處理常式**|選取此功能表或 [索引標籤] 選項視圖，以查看與所選活動相關聯的[FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) 。|
|**查看補償處理常式**|選取此功能表或 [索引標籤] 選項視圖，以查看與所選[TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)相關聯的[CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) 。|
|**View 事件處理常式**|選取此功能表或 [索引標籤] 選項視圖，以查看與所選[EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)相關聯的[EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) 。|

 如需類似視圖的詳細資訊，請參閱[連續工作流程視圖（舊版）](../workflow-designer/sequential-workflow-views-legacy.md)。

## <a name="see-also"></a>請參閱
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)[順序工作流程流覽（舊版）](../workflow-designer/sequential-workflow-views-legacy.md)
