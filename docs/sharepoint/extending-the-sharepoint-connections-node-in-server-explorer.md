---
title: 擴充 SharePoint 連線節點，在 [伺服器總管] |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 433923234b890564d21915d56a906fe10060e4ae
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766268"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>擴充 SharePoint 連線節點，在 伺服器總管
  在 Visual Studio 中，您可以連接到開發電腦上的本機 SharePoint 網站使用**SharePoint 連接**節點**伺服器總管**視窗。 此節點會顯示許多元件的本機 SharePoint 網站中的階層式樹狀檢視。 例如，您可以在本機站台上檢視清單、 文件庫和內容類型。 如需有關使用**伺服器總管**若要連接至本機 SharePoint 網站，請參閱[瀏覽 SharePoint 連線使用伺服器總管](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)。  
  
 您可以擴充**SharePoint 連接**藉由建立延伸現有的節點，或藉由建立自訂節點類型，並將它加入至節點之階層的節點。  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>擴充 SharePoint 連線節點的工作
 若要擴充現有的節點，建立 Visual Studio 擴充功能實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>介面。 當您擴充節點時，您可以將功能加入節點，例如您自己的快顯功能表項目或自訂屬性。 如需詳細資訊，請參閱[如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
 若要建立自訂節點類型，建立 Visual Studio 擴充功能實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>介面。 如果您想要顯示的不會顯示在 SharePoint 站台的元件建立自訂節點**伺服器總管**預設。 例如，**伺服器總管**不的顯示的網頁組件庫中的 SharePoint 網站的預設值，但是您可以加入此自訂節點。 如需詳細資訊，請參閱[How to： 自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)和[逐步解說： 擴充伺服器總管 來顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## <a name="add-custom-properties-to-nodes"></a>將自訂屬性加入至節點
 當您擴充節點，或建立自訂節點類型時，您可以加入自訂屬性的節點。 屬性會出現在**屬性**視窗選取節點時。  
  
 有兩種類型的自訂屬性，您可以加入到節點：  
  
-   顯示一組的唯讀資料，從 SharePoint 網站的內容。 資料描述，則節點代表 SharePoint 元件。 如需示範如何執行此動作的逐步解說，請參閱[逐步解說： 擴充伺服器總管 來顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   顯示自訂的讀取/寫入資料的屬性。 如需程式碼範例示範如何執行這項操作，請參閱[如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## <a name="get-data-for-built-in-nodes"></a>取得內建的節點中的資料
 所有 Visual Studio 所提供的內建節點包含它們所代表的 SharePoint 元件有關的一些資料。 例如，節點，表示 SharePoint 網站上的清單提供有關清單中，例如標題和清單的預設檢視的 URL 的一些資料。  
  
 若要存取此資料，擷取中的資料物件<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>物件，表示您感興趣的節點。 資料物件的類型取決於節點的類型。  
  
 下列程式碼範例示範如何取得清單節點的資料物件。 若要查看這個內容中的較大範例的範例，請參閱[How to： 取得資料，在伺服器總管 中的內建 SharePoint 節點](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 下表列出每個內建的節點類型的資料物件類型。  
  
|節點類型|資料物件類型|  
|---------------|----------------------|  
|SharePoint 網站 節點|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|內容類型|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|功能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|欄位|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|清單|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|清單範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|清單檢視 (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|工作流程關聯|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|工作流程範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 如需有關使用<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性，請參閱[關聯自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## <a name="see-also"></a>另請參閱
 [逐步解說： 擴充伺服器總管 以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [如何： 自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [如何： 取得伺服器總管 中的內建 SharePoint 節點資料](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [關聯自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [使用 伺服器總管瀏覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  
