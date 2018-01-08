---
title: "擴充 SharePoint 專案項目 |Microsoft 文件"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ffbacd5748ae2a5284ed628dce974b20e25bcab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extending-sharepoint-project-items"></a>擴充 SharePoint 專案項目
  建立專案項目擴充功能，當您想要將功能加入至已安裝 Visual Studio 中的 SharePoint 專案項目的型別。 例如，您可以建立擴充功能為內建**事件接收器**或**清單定義**專案項目在 Visual Studio 中，或者您可以建立自訂專案項目類型的擴充功能。 您也可以建立適用於所有類型的 SharePoint 專案項目延伸模組。  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>擴充 SharePoint 專案項目工作  
 若要擴充的專案項目，建置 Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>介面。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
 當您擴充專案項目時，您也可以加入下列功能的專案項目：  
  
-   將捷徑功能表項目加入至專案項目。 當您開啟專案項目中的捷徑功能表，出現的功能表項目**方案總管 中**。 以滑鼠右鍵按一下專案項目開啟捷徑功能表，或選擇它，然後選擇 Shift + F10 鍵。 如需詳細資訊，請參閱[How to： 將捷徑功能表項目加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)。  
  
-   將自訂屬性加入至專案項目。 屬性會出現在**屬性**視窗時選擇的專案項目**方案總管 中**。 如需詳細資訊，請參閱[How to： 將屬性加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)。  
  
 如需示範如何建立、 部署和測試專案項目擴充功能的逐步解說，請參閱[逐步解說： 擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)。  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>了解專案項目擴充功能和專案項目執行個體之間的關聯性  
 當您建立專案項目擴充功能時，Visual Studio 的專案項目相關聯的類型加入至 SharePoint 專案時，就會載入您的擴充功能。 例如，如果您建立的延伸模組**事件接收器**專案項目，Visual Studio 會載入您的擴充功能時，使用者將**事件接收器**專案項目加入專案。 Visual Studio 會使用您的擴充功能的相同執行個體相關聯的專案項目類型的所有執行個體。 在上述範例中，如果使用者加入第二個**事件接收器**專案項目加入專案中，您的擴充功能的相同執行個體用於自訂的第二個專案項目。  
  
 若要存取所擴充的專案項目類型的特定執行個體，處理其中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>事件*projectItemType*的實作中的參數<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法。 例如，若要判斷所擴充之類型的專案項目加入至專案時，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>事件。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint 專案項目識別碼  
 每個 SharePoint 專案項目都有對應的字串識別碼。 您必須知道的識別項的專案項目，如果您想要執行下列工作：  
  
-   建立專案項目擴充功能。 在此情況下，您必須傳遞專案項目，您想要延伸的建構函式的識別項<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 若要建立所有專案項目類型擴充功能，將傳遞 **\*** 字串值。  
  
-   以程式設計方式將專案項目加入專案。 在此情況下，您必須傳遞的專案項目識別項<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>方法。  
  
 下表列出隨附於 Visual Studio SharePoint 專案項目識別項。  
  
|專案項目名稱|字串識別項|  
|-----------------------|-----------------------|  
|商務資料目錄模型|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|內容類型|Microsoft.VisualStudio.SharePoint.ContentType|  
|事件接收器|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空元素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|清單定義<br /><br /> 從內容類型的清單定義|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|清單執行個體|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|循序性工作流程<br /><br /> 狀態機器工作流程|Microsoft.VisualStudio.SharePoint.Workflow|  
|網站定義|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|視覺 Web 組件|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|網頁組件|Microsoft.VisualStudio.SharePoint.WebPart|  
|工作流程關聯表單|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>請參閱  
 [如何： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何： 將捷徑功能表項目加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [如何： 將屬性加入 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [逐步解說： 擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)  
  