---
title: 連續工作流程查看（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 859fa44b44a295dc3e9f27fc168092a9fe2beebf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292360"
---
# <a name="sequential-workflow-views-legacy"></a>循序工作流程檢視 (舊版)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] 提供可用來以 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]為目標的舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)]。

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 提供了一種以圖形方式使用熟悉的 [!INCLUDE[wf](../includes/wf-md.md)] 使用者介面建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 應用程式。 [!INCLUDE[wf](../includes/wf-md.md)] 應用程式是由稱做活動的工作流程程序步驟所組成。 若要建立工作流程，請在設計介面上撰寫活動，方法是將其各自的活動設計工具從 [**工具箱**] 拖曳至設計介面上。

 當您建立連續工作流程（這是[SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)）時，會有三個工作流程的觀點。 這些視圖可從 [**工作流程**] 功能表和設計介面上的內容功能表存取。

 下表列出每個檢視的名稱和說明。

|功能表/索引標籤選項|描述|
|----------------------|-----------------|
|**View SequentialWorkflow**|以滑鼠右鍵按一下設計介面，然後從內容功能表中選取 [ **View SequentialWorkflow** ] 選項，以顯示 [**連續工作流程**] 視圖，其中會顯示以活動為基礎的順序工作流程圖形表示。 或者，從 [**工作流程**] 功能表中選取 [ **View SequentialWorkflow** ]。|
|**View 取消處理常式**|以滑鼠右鍵按一下設計介面，然後從內容功能表中選取 [ **View 取消處理常式**] 選項，以顯示 [**連續工作流程**] 視圖，其中會顯示與工作流程相關聯的[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)活動。 或者，從 [**工作流程**] 功能表中選取 [ **View 取消處理常式**]。|
|**查看錯誤處理常式**|以滑鼠右鍵按一下設計介面，然後從操作功能表中選取 [ **View 錯誤處理常式**] 選項，以顯示 [**錯誤**] 視圖，其中會顯示與工作流程相關聯的[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)活動。 或者，從 [**工作流程**] 功能表選取 [**查看錯誤處理常式**]。|

 如需類似視圖的詳細資訊，請參閱[即時檢視（舊版）](../workflow-designer/activity-views-legacy.md)。

## <a name="see-also"></a>另請參閱
 [即時檢視（舊版）](../workflow-designer/activity-views-legacy.md) [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)[工作流程撰寫模式](https://go.microsoft.com/fwlink?LinkID=65014)