---
title: 在工作流程中形成支援 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b3a07f56819818e55548292f3dbcdc1095d9f00
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326076"
---
# <a name="form-support-in-workflows"></a>在工作流程中的表單支援
  表單的四種可用工作流程中： 關聯、 初始化、 工作及修改。 這些表單類型可以根據 ASPX 表單或 InfoPath 表單。 支援層級[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供特定的格式取決於許多因素下, 表所述。 如需工作流程表單類型的詳細資訊，請參閱[工作流程表單概觀](http://go.microsoft.com/fwlink/?LinkId=185228)MSDN 網站上。  
  
## <a name="xml-refactoring"></a>XML 重構
 當您將加入到 ASPX 關聯或初始表單[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]工作流程專案項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]自動重構的工作流程中的 XML *Elements.xml*保留屬性參考到關聯的檔案或同步更新表單的名稱或部署路徑時的初始表單已刪除。 不過，當您使用其他表單類型工作流程工作或修改的形式，例如*Elements.xml*檔案不在重構。  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>新的 Visual Studio 工作流程中的表單支援
 下表列出[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中建立的工作流程中的 ASPX 或 InfoPath 表單上的不同表單類型的支援[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
|為表單類型|Visual Studio 中使用 ASPX 表單建立工作流程|使用 InfoPath 表單在 Visual Studio 中建立的工作流程|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|關聯|-ASPX 關聯表單可以使用 加入至工作流程**工作流程關聯表單**項目範本。<br />- *Elements.xml*當表單加入、 重新命名或刪除，或它的部署路徑變更時，已重構的工作流程檔案。<br />-如需詳細資訊，請參閱[逐步解說： 使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-沒有在沒有 InfoPath 關聯表單範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath Designer。<br />- *Elements.xml*工作流程的檔案不在重構。|  
|起始|-ASPX 初始表單可以使用 加入至工作流程**工作流程初始表單**項目範本。<br />- *Elements.xml*當表單加入、 重新命名或刪除，或它的部署路徑變更時，已重構的工作流程檔案。<br />-如需詳細資訊，請參閱[逐步解說： 使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-沒有在沒有 InfoPath 關聯表單範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath Designer。<br />- *Elements.xml*工作流程的檔案不在重構。|  
|工作|-沒有 ASPX 工作表單範本位於[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 您必須建立應用程式頁面，並加入程式碼。<br />- *Elements.xml*工作流程的檔案不在重構。<br />-如需詳細資訊，請參閱[工作流程工作表單 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-沒有在沒有 InfoPath 工作表單範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath Designer。<br />- *Elements.xml*工作流程的檔案不在重構。|  
|修改|-沒有 ASPX 修改表單範本位於[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 若要新增修改表單，您必須建立應用程式頁面，並加入程式碼。<br />- *Elements.xml*工作流程的檔案不在重構。 您必須手動編輯適當。<br />-如需詳細資訊，請參閱[工作流程修改表單 (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-沒有在沒有 InfoPath 修改表單範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。<br />-沒有之間整合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 InfoPath Designer。<br />- *Elements.xml*工作流程的檔案不在重構。|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>匯入 SharePoint 可重複使用的工作流程中的表單支援
 下表列出[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]匯入至的 SharePoint 可重複使用工作流程中的 ASPX 或 InfoPath 表單上的不同表單類型的支援[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
|為表單類型|可重複使用已匯入從 SharePoint Designer ASPX 表單的工作流程|可重複使用已從 SharePoint Designer 匯入 InfoPath 表單的工作流程|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|關聯|-在表單中會參考*Elements.xml*工作流程檔案。<br />- *Elements.xml*當表單重新命名或刪除，或它的部署路徑變更時，已重構的工作流程檔案。|-表單會匯入，但不是能以參考*Elements.xml*工作流程。<br />- *Elements.xml*工作流程的檔案不在重構。|  
|起始|-在表單中的工作流程所參考*Elements.xml*工作流程檔案。<br />- *Elements.xml*當表單重新命名或刪除，或它的部署路徑變更時，已重構的工作流程檔案。|-表單會匯入，但不是能以參考*Elements.xml*工作流程。<br />- *Elements.xml*工作流程的檔案不在重構。 **注意：** 規則和屬性必須新增和變更這個案例運作。|  
|工作|-在表單中會參考*Elements.xml*工作流程檔案。<br />- *Elements.xml*工作流程的檔案不在重構。|-表單會匯入，但不是能以參考*Elements.xml*工作流程。<br />- *Elements.xml*工作流程的檔案不在重構。 **注意：** 規則和屬性必須新增和變更這個案例運作。|  
|修改|不適用。 無法在 SharePoint Designer 建立 ASPX 修改表單。|不適用。 除了內建的 SharePoint 伺服器工作流程，其中不包含.wsp 檔案中匯出工作流程時，無法在 SharePoint Designer 建立 InfoPath 修改表單。|  
  
## <a name="see-also"></a>另請參閱
 [逐步解說： 使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
