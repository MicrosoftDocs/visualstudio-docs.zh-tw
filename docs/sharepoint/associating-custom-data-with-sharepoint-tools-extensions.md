---
title: 關聯自訂資料與 SharePoint 工具擴充功能 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0507fe16dd910fe61c4816594125b690c350a1a6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691366"
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>關聯自訂資料與 SharePoint 工具擴充功能
  您可以加入自訂資料中 SharePoint 工具擴充功能的特定物件。 當您想要從您的擴充功能中的其他程式碼供稍後存取的擴充功能的一個部分中有資料時，這非常有用。 而是實作自訂的方式來儲存及存取資料，您可以關聯物件中的資料，在您的擴充功能，然後稍後從相同的物件擷取資料。  
  
 加入自訂資料物件時也很有用您想要保留的 Visual Studio 中的特定項目相關資料。 SharePoint 工具擴充功能會載入一次在 Visual Studio 中，因此您的擴充功能可能會使用數個不同的項目 (例如專案、 專案項目，或**伺服器總管**節點) 在任何時間。 如果您有只與特定的項目有關的自訂資料，您可以將資料加入物件，表示該項目。  
  
 當您新增自訂資料物件中 SharePoint 工具擴充功能時，就不會保存資料。 只有在物件的存留期間有可用資料。 透過記憶體回收收回物件之後，資料會遺失。  
  
 擴充功能的 SharePoint 專案系統，您也可以儲存字串資料保存在卸載擴充功能之後。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統中儲存的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## <a name="objects-that-can-contain-custom-data"></a>可以包含自訂資料物件
 您可以加入實作 SharePoint 工具物件模型中的任何物件中的自訂資料<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>介面。 這個介面會定義一個屬性， <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>，這是自訂的資料物件的集合。 下列型別會實作<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>加入和擷取自訂的資料
 若要加入自訂資料中的 SharePoint 工具擴充功能的物件，取得<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>您想要新增的資料，然後使用的物件屬性<xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A>方法，將資料加入至物件。  
  
 若要從 SharePoint 工具擴充功能中的物件擷取自訂的資料，取得<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性物件，然後使用其中一個的下列方法：  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. 這個方法會傳回**true**如果資料物件存在，或**false**如果不存在。 您可以使用這個方法來擷取實值類型或參考類型的執行個體。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. 這個方法傳回的資料物件，如果它存在時，或**null**如果不存在。 您可以使用這個方法，才能擷取參考類型的執行個體。  
  
 下列程式碼範例會判斷特定資料物件是否已經與專案項目相關聯。 如果資料物件是不相關聯的專案項目，則程式碼將物件加入<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>專案項目的屬性。 若要查看這個內容中的較大範例的範例，請參閱[How to： 將屬性加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>另請參閱
 [SharePoint 工具擴充功能的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說： 擴充伺服器總管 以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [如何： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [如何： 將屬性加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md   
 