---
title: "循序工作流程檢視 （舊版） |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9f412fa9afee6aa768447fc226553fd68970e646
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="sequential-workflow-views-legacy"></a>循序工作流程檢視 (舊版)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 提供舊版的 Windows 工作流程設計工具的可用目標[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]或[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 提供了一種以圖形方式使用熟悉的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 使用者介面建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 應用程式。 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式是由稱做活動的工作流程程序步驟所組成。 若要建立工作流程，撰寫活動在設計介面上的拖曳其各自的活動設計工具從**工具箱**拖曳至設計介面。

 當您建立循序工作流程，也就是[SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)，也可使用三個工作流程的檢視。 這些檢視表是可從存取**工作流程**功能表和設計介面上的內容功能表。

 下表列出每個檢視的名稱和說明。

|功能表/索引標籤選項|描述|
|----------------------|-----------------|
|**檢視 SequentialWorkflow**|以滑鼠右鍵按一下設計介面，並選取**檢視 SequentialWorkflow**從內容功能表選項以顯示**循序工作流程**檢視會顯示活動的圖形表示循序工作流程。 或選取**檢視 SequentialWorkflow**從**工作流程**功能表。|
|**檢視取消處理常式**|以滑鼠右鍵按一下設計介面，並選取**檢視取消處理常式**從內容功能表選項以顯示**循序工作流程**檢視檢視會顯示[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)與工作流程關聯的活動。 或選取**檢視取消處理常式**從**工作流程**功能表。|
|**檢視錯誤處理常式**|以滑鼠右鍵按一下設計介面，並選取**檢視錯誤處理常式**從內容功能表選項以顯示**錯誤**檢視檢視會顯示[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)與工作流程關聯的活動。 或選取**檢視錯誤處理常式**從**工作流程**功能表。|

 如需類似的檢視的詳細資訊，請參閱[活動檢視 （舊版）](../workflow-designer/activity-views-legacy.md)。

## <a name="see-also"></a>另請參閱

- [活動檢視 (舊版)](../workflow-designer/activity-views-legacy.md)
- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)
- [工作流程撰寫模式](http://go.microsoft.com/fwlink?LinkID=65014)