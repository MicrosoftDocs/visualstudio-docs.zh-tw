---
title: 如何：將新的專案加入至工作流程專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656625"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>HOW TO：將新的項目加入至工作流程專案
在建立工作流程專案後，可以將工作流程活動、設計工具和其他熟悉的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 項目加入至專案。

 下表列出您可加入至工作流程專案的 [!INCLUDE[wf](../includes/wf-md.md)] 項目。

|Name|描述|
|----------|-----------------|
|活動|要由其他活動組成的活動。 選取這個專案會將相同的 XAML 檔案加入至專案，就像您在選取新專案的 **活動程式庫** 範本時所取得的一樣。 [!INCLUDE[crabout](../includes/crabout-md.md)] 在此程式中，請參閱 how [to：建立活動程式庫](../workflow-designer/how-to-create-an-activity-library.md)。|
|活動設計工具|可自訂活動之設計階段經驗的設計工具。 選取這個專案會將相同的檔案加入至專案，就像您在選取新專案的 [ **活動設計** 工具程式庫] 範本時所取得的一樣。 [!INCLUDE[crabout](../includes/crabout-md.md)] 在這個程式中，請參閱 [如何：建立活動設計](../workflow-designer/how-to-create-an-activity-designer-library.md)工具程式庫。|
|程式碼活動|包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。|
|WCF 工作流程服務|使用工作流程活動建置的 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 服務。 選取這個專案會將相同的檔案加入至專案，就像您在選取新專案的 **WCF Workflow Service 應用程式** 範本時所取得的一樣。 [!INCLUDE[crabout](../includes/crabout-md.md)] 在此程式中，請參閱 [如何：建立 WCF 工作流程服務應用程式](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)。|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1. 在 [ **專案** ] 功能表上，按一下 [ **加入新專案 ...**]。

     [ **加入新專案** ] 對話方塊隨即開啟。

2. 在 [ **已安裝的範本** ] 窗格中，選取 [ **工作流程** 群組]。

3. 選取四個項目的其中一個。 上表列出可用的選擇。

4. 在對話方塊底部的 [ **名稱** ] 方塊中，為專案輸入適當的名稱。

5. 按一下 [ **加入** ]，將專案加入至目前的工作流程專案。

## <a name="see-also"></a>另請參閱
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)