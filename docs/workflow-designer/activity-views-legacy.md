---
title: 工作流程設計工具的活動檢視 （舊版）
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d3453ecefece93f593c3d4ebbc261e4332815da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970330"
---
# <a name="activity-views-legacy"></a>活動檢視 (舊版)

許多活動，提供由 Windows Workflow Foundation (WF)，從工作流程由所組成，有幾個舊版的 Windows 工作流程設計工具中可用的設計檢視。 當您拖曳的活動設計工具**工具箱**拖曳至設計介面，以及此後每次選取活動時，您可以在使用不同的設計檢視之間切換**工作流程**功能表或以滑鼠右鍵按一下選取的活動。 此外，當您將指標移至選取活動的名稱上方時，會顯示一組下拉式索引標籤，可用來在不同的檢視之間切換。

每個活動有至少一個檢視。這是顯示當您拖曳的活動設計工具的預設檢視**工具箱**拖曳至設計介面。 此活動預設檢視中可做為**檢視 [活動類型]** 選項功能表和索引標籤上，例如**檢視 Parallel**。 大部分的活動會有額外的檢視，不同的活動可以有不同的檢視。 例如， [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)活動有補償檢閱和[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)活動有事件檢視。 許多隨附於 Windows Workflow Foundation 活動都有**檢視取消處理常式**和**檢視錯誤**設計檢視來檢視[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)和[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與其相關聯。

下表列出每個檢視的名稱和說明。

|功能表/索引標籤選項|描述|
|----------------------|-----------------|
|**檢視 [活動類型]**|選取此功能表或索引標籤選項可檢視所選活動的預設圖形表示。|
|**檢視取消處理常式**|選取此功能表或索引標籤選項可檢視[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)與所選活動相關聯。|
|**檢視錯誤處理常式**|選取此功能表或索引標籤選項可檢視[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與所選活動相關聯。|
|**檢視補償處理常式**|選取此功能表或索引標籤選項可檢視[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)選取相關聯[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)。|
|**檢視事件處理常式**|選取此功能表或索引標籤選項可檢視[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)選取相關聯[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)。|

類似的檢視表的相關資訊，請參閱[循序工作流程檢視 （舊版）](../workflow-designer/sequential-workflow-views-legacy.md)。

## <a name="see-also"></a>另請參閱

- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)
- [循序工作流程檢視 (舊版)](../workflow-designer/sequential-workflow-views-legacy.md)