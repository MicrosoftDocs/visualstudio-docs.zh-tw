---
title: 如何： 將新的項目新增至工作流程專案 （舊版） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 26be9519a4f9ee496ea36a61debffec7f96ffbe5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301154"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>HOW TO：將新的項目加入至工作流程專案 (舊版)
當您使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 所提供的舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來建立工作流程專案時 (此專案是以 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 為目標)，您可以將 [!INCLUDE[wf](../includes/wf-md.md)] 項目和其他熟悉的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 項目加入專案中。  
  
 下表列出您可加入至工作流程專案的 [!INCLUDE[wf2](../includes/wf2-md.md)] 項目。  
  
|項目|描述|  
|----------|-----------------|  
|活動|活動定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的活動。|  
|活動 (程式碼分開置放)|活動定義表示成工作流程標記，且使用者程式碼置於不同的程式碼檔案。|  
|循序工作流程 (程式碼)|工作流程定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的循序工作流程。|  
|循序工作流程 (程式碼分開置放)|工作流程定義表示成工作流程標記，且使用者程式碼置於不同程式碼檔案的循序工作流程。|  
|狀態機器工作流程 (程式碼)|工作流程定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的狀態機器工作流程。|  
|狀態機器工作流程 (程式碼分開置放)|工作流程定義表示成工作流程標記，且使用者程式碼置於不同程式碼檔案的狀態機器工作流程。|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案  
  
1.  在 **專案**功能表上，按一下**加入新項目**。  
  
     **加入新項目**對話方塊隨即開啟。  
  
2.  選取項目。  
  
     上表列出可用的 Windows Workflow Foundation 選擇。  
  
3.  按一下 **新增**將項目新增至工作流程專案。  
  
## <a name="see-also"></a>另請參閱  
 [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)