---
title: 擴充 SharePoint 專案項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d02871b991c999c490aac8aaeafc677711c95266
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959957"
---
# <a name="extend-sharepoint-project-items"></a>擴充 SharePoint 專案項目
  當您想要將功能新增至已安裝 Visual Studio 中的 SharePoint 專案項目類型，請建立專案項目擴充功能。 比方說，您可以在其中建立內建的擴充功能**事件接收器**或是**清單定義**專案項目在 Visual Studio 中，或者您可以建立自訂專案項目類型的擴充功能。 您也可以建立所有 SharePoint 專案項目類型的擴充功能。  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>擴充 SharePoint 專案項目工作
 若要擴充的專案項目，建置 Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>介面。 如需詳細資訊，請參閱[＜How to：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
 當您擴充的專案項目時，您也可以在專案項目，新增下列功能：  
  
- 快顯功能表項目加入專案項目。 當您開啟快顯功能表中的專案項目時，會出現的功能表項目**方案總管 中**。 您開啟捷徑功能表，以滑鼠右鍵按一下專案項目，或選擇它，然後選擇**Shift**+**F10**索引鍵。 如需詳細資訊，請參閱[＜How to：將捷徑功能表項目新增至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)。  
  
- 將自訂屬性加入專案項目。 屬性會出現在**屬性**視窗中，當您選擇的專案項目時**方案總管 中**。 如需詳細資訊，請參閱[＜How to：將屬性加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)。  
  
  如需示範如何建立、 部署和測試專案項目擴充功能的逐步解說，請參閱[逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)。  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>了解專案項目擴充功能和專案項目執行個體之間的關聯性
 當您建立專案項目擴充功能時，Visual Studio 相關聯的類型的專案項目新增至 SharePoint 專案時，就會載入您的延伸模組。 例如，如果您建立的擴充功能**事件接收器**專案項目，Visual Studio 會載入您的延伸模組當使用者將**事件接收器**至專案的專案項目。 Visual Studio 會使用您的擴充功能的相同執行個體相關聯的專案項目類型的所有執行個體。 在上述範例中，如果使用者加入第二個**事件接收器**專案項目至專案，您的擴充功能的相同執行個體用來自訂的第二個專案項目。  
  
 若要存取您要擴充的專案項目類型的特定執行個體，處理的其中一個<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>的事件*projectItemType*實作中的參數<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法。 例如，若要判斷您要擴充類型的專案項目新增至專案時，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>事件。 如需詳細資訊，請參閱[＜How to：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint 專案項目識別碼
 每個 SharePoint 專案項目有對應的字串識別項。 您必須知道專案項目的識別碼，如果您想要執行下列工作：  
  
- 建立專案項目的延伸模組。 在此情況下，您必須傳遞您想要擴充的建構函式的專案項目識別碼<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 若要針對所有專案項目類型，請建立擴充功能，傳遞**\\*** 字串值。  
  
- 以程式設計方式將專案項目加入至專案。 在此情況下，您必須傳遞的專案項目識別碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>方法。  
  
  下表列出隨附於 Visual Studio SharePoint 專案項目的識別碼。  
  
|專案項目名稱|字串識別碼|  
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
  
## <a name="see-also"></a>另請參閱
 [如何：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何：將捷徑功能表項目新增至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [如何：將屬性加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)  
