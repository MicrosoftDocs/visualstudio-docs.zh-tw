---
title: "在工作流程中形成支援 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0da90955a590881a02117213246e580339dbe596
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="form-support-in-workflows"></a>工作流程中的表單支援
  表單的四種可用工作流程中： 關聯、 初始化、 工作及修改。 這些表單類型可以根據 ASPX 表單或表單。 支援層級[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供特定的格式取決於許多因素下, 表所述。 如需工作流程表單類型的詳細資訊，請參閱[Workflow Form 概觀](http://go.microsoft.com/fwlink/?LinkId=185228)MSDN 網站上。  
  
## <a name="xml-refactoring"></a>XML 重構  
 當您將加入至 ASPX 關聯或初始表單[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]工作流程專案項目，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]自動重構工作流程的 Elements.xml 檔案中的 XML，保留指的是關聯或起始同步處理的表單屬性每當更新表單名稱或部署路徑或表單刪除。 不過，當您使用工作流程，例如工作或修改表單中的其他表單類型 Elements.xml 檔案，將會無法重構。  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>新的 Visual Studio 工作流程中的表單支援  
 下表列出[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ASPX 或 InfoPath 表單中建立的工作流程中不同的表單類型的支援[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
|表單型別|Visual Studio 中使用 ASPX 表單建立工作流程|在 Visual Studio 中使用建立的 InfoPath 表單的工作流程|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|關聯|-ASPX 關聯表單可以加入至工作流程使用**工作流程關聯表單**項目範本。<br />-當表單加入、 重新命名或刪除，或其部署路徑變更時，將會重構 Elements.xml 檔案的工作流程。<br />-如需詳細資訊，請參閱[逐步解說： 建立工作流程關聯與初始化表單與](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-沒有 InfoPath 關聯表單範本中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間沒有整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 設計師。<br />-無法重構 Elements.xml 檔案的工作流程。|  
|初始化|-ASPX 初始表單可以加入至工作流程使用**工作流程初始表單**項目範本。<br />-當表單加入、 重新命名或刪除，或其部署路徑變更時，將會重構 Elements.xml 檔案的工作流程。<br />-如需詳細資訊，請參閱[逐步解說： 建立工作流程關聯與初始化表單與](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-沒有 InfoPath 關聯表單範本中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間沒有整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 設計師。<br />-無法重構 Elements.xml 檔案的工作流程。|  
|工作|-沒有 ASPX 工作表單範本可用於[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 您必須建立應用程式頁面上，並加入程式碼。<br />-無法重構 Elements.xml 檔案的工作流程。<br />-如需詳細資訊，請參閱[工作流程工作表單 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-沒有在 InfoPath 工作表單範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間沒有整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 設計師。<br />-無法重構 Elements.xml 檔案的工作流程。|  
|修改|-沒有 ASPX 修改表單範本可用於[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要新增修改表單，您必須建立應用程式頁面上，並加入程式碼。<br />-無法重構 Elements.xml 檔案的工作流程。 您必須手動編輯適當。<br />-如需詳細資訊，請參閱[工作流程修改表單 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-沒有中的修改 InfoPath 表單範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間沒有整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath 設計師。<br />-無法重構 Elements.xml 檔案的工作流程。|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>在匯入的 SharePoint 可重複使用工作流程中的表單支援  
 下表列出[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ASPX 或 InfoPath 表單 SharePoint 可重複使用的工作流程會匯入至不同的表單類型的支援[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
|表單型別|已從 SharePoint Designer 匯入 ASPX 表單的可重複使用工作流程|已從 SharePoint Designer 匯入的 InfoPath 表單的可重複使用工作流程|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|關聯|-表單是在工作流程的 Elements.xml 檔案中參考。<br />-當您重新命名或刪除，表單或其部署路徑變更時，將會重構 Elements.xml 檔案的工作流程。|-表單是匯入，但在工作流程的 Elements.xml 並未參考。<br />-無法重構 Elements.xml 檔案的工作流程。|  
|初始化|-表單正由工作流程的 Elements.xml 檔案中的工作流程。<br />-當您重新命名或刪除，表單或其部署路徑變更時，將會重構 Elements.xml 檔案的工作流程。|-表單是匯入，但在工作流程的 Elements.xml 並未參考。<br />-無法重構 Elements.xml 檔案的工作流程。 **注意：**規則和屬性必須新增並變更此案例要能運作。|  
|工作|-表單是在工作流程的 Elements.xml 檔案中參考。<br />-無法重構 Elements.xml 檔案的工作流程。|-表單是匯入，但在工作流程的 Elements.xml 並未參考。<br />-無法重構 Elements.xml 檔案的工作流程。 **注意：**規則和屬性必須新增並變更此案例要能運作。|  
|修改|不適用。 無法在 SharePoint Designer 中建立 ASPX 修改表單。|不適用。 除了內建的 SharePoint 伺服器工作流程，後者不包含.wsp 檔案中匯出的工作流程時，無法在 SharePoint Designer 中建立 InfoPath 修改表單。|  
  
## <a name="see-also"></a>請參閱  
 [逐步解說： 使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  