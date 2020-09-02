---
title: " (舊版) 的連續工作流程視圖 |Microsoft Docs"
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
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846207"
---
# <a name="sequential-workflow-views-legacy"></a>循序工作流程檢視 (舊版)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] 提供 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 可以用來將或設為目標的舊版 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 。

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 提供了一種以圖形方式使用熟悉的 [!INCLUDE[wf](../includes/wf-md.md)] 使用者介面建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 應用程式。 [!INCLUDE[wf](../includes/wf-md.md)] 應用程式是由稱做活動的工作流程程序步驟所組成。 若要建立工作流程，請從 [工具箱] 將活動設計 **工具** 拖曳至設計介面，以在設計介面上撰寫活動。

 當您建立連續工作流程（也就是 [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)）時，可以使用工作流程的三個視圖。 您可以從 [ **工作流程** ] 功能表和設計介面上的內容功能表來存取這些視圖。

 下表列出每個檢視的名稱和說明。

|功能表/索引標籤選項|描述|
|----------------------|-----------------|
|**檢視 SequentialWorkflow**|以滑鼠右鍵按一下設計介面，然後從操作功能表中選取 [ **View SequentialWorkflow] （View** ）選項，以顯示 [ **連續工作流程** ] 視圖，顯示以活動為基礎的連續工作流程圖形表示。 或從 [**工作流程**] 功能表中選取 [ **View SequentialWorkflow** ]。|
|**檢視取消處理常式**|以滑鼠右鍵按一下設計介面，然後從內容功能表中選取 [ **View Cancel 處理常式** ] 選項，以顯示 [ **順序工作流程** ] 視圖，顯示與工作流程相關聯的 [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) 活動。 或者，從 [**工作流程**] 功能表中選取 [ **View Cancel Handler** ]。|
|**檢視錯誤處理常式**|以滑鼠右鍵按一下設計介面，然後從內容功能表中選取 [ **視圖錯誤處理常式** ] 選項，以顯示 [ **錯誤** ] 視圖，顯示與工作流程相關聯的 [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) 活動。 或選取 [**工作流程**] 功能表中的 [**查看錯誤處理常式**]。|

 如需類似視圖的詳細資訊，請參閱 [ (舊版) 的即時檢視 ](../workflow-designer/activity-views-legacy.md)。

## <a name="see-also"></a>另請參閱
 [即時檢視 (舊版) ](../workflow-designer/activity-views-legacy.md) [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)[工作流程撰寫模式](https://msdn2.microsoft.com/library/bb628440.aspx)
