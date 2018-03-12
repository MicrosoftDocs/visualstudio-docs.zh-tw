---
title: "如何： 將新的項目加入至工作流程專案 （舊版） |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d2b0c644854f8f08ff7aeeb05f92fe3fd359f45e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>HOW TO：將新的項目加入至工作流程專案 (舊版)
建立工作流程專案使用舊版所提供的 Windows 工作流程設計工具之後[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]為目標[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]或[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]，您可以加入[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]項目和其他熟悉[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]項目到您專案。

 下表列出您可加入至工作流程專案的 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 項目。

|項目|描述|
|----------|-----------------|
|活動|活動定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的活動。|
|活動 (程式碼分開置放)|活動定義表示成工作流程標記，且使用者程式碼置於不同的程式碼檔案。|
|循序工作流程 (程式碼)|工作流程定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的循序工作流程。|
|循序工作流程 (程式碼分開置放)|工作流程定義表示成工作流程標記，且使用者程式碼置於不同程式碼檔案的循序工作流程。|
|狀態機器工作流程 (程式碼)|工作流程定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的狀態機器工作流程。|
|狀態機器工作流程 (程式碼分開置放)|工作流程定義表示成工作流程標記，且使用者程式碼置於不同程式碼檔案的狀態機器工作流程。|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1.  在**專案**功能表上，按一下 **加入新項目**。

     **加入新項目**對話方塊隨即開啟。

2.  選取項目。

     上表列出可用的 Windows Workflow Foundation 選擇。

3.  按一下**新增**將項目加入至工作流程專案。

## <a name="see-also"></a>另請參閱

- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)