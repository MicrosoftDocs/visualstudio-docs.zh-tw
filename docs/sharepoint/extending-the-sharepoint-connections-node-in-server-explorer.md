---
title: 擴充 SharePoint 連線節點，在 伺服器總管 |Microsoft Docs
ms.date: 02/02/2017
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
ms.openlocfilehash: 36e99b5d239b48add1de5c281c35e698607500d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933923"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>擴充 SharePoint 連線節點，在 伺服器總管
  在 Visual Studio 中，您可以連接至本機 SharePoint 網站，在開發電腦上使用**SharePoint 連線**中的節點**伺服器總管**視窗。 這個節點會顯示在階層樹狀結構檢視中的許多元件的本機 SharePoint 網站。 例如，您可以在本機的站台上檢視清單、 文件庫和內容類型。 如需使用詳細資訊**伺服器總管**若要連線至本機 SharePoint 網站，請參閱[使用伺服器總管瀏覽 SharePoint 連線](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)。  
  
 您可以延伸**SharePoint 連線**藉由建立擴充功能，為現有的節點，或藉由建立自訂節點類型，並將它新增至節點的階層節點。  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>擴充 SharePoint 連線節點的工作
 若要擴充現有的節點，建立 Visual Studio 擴充功能實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>介面。 當您擴充節點時，您可以加入功能，例如您自己的快顯功能表項目或自訂屬性的節點。 如需詳細資訊，請參閱[＜How to：擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
 若要建立自訂節點類型，建立 Visual Studio 擴充功能實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>介面。 建立自訂的節點，如果您想要顯示的 SharePoint 網站，不會顯示在元件**伺服器總管**預設。 例如，**伺服器總管**不會的顯示 Web 組件庫的 SharePoint 網站的預設值，但您可以新增此自訂節點。 如需詳細資訊，請參閱[＜How to：自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)和[逐步解說：擴充伺服器總管以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## <a name="add-custom-properties-to-nodes"></a>將自訂屬性新增至節點
 當您擴充節點，或建立自訂節點類型時，您可以新增自訂屬性至節點。 屬性會出現在**屬性**視窗中選取節點時。  
  
 有兩種類型的自訂屬性，您可以將節點加入：  
  
-   顯示一組從 SharePoint 網站的唯讀資料的屬性。 資料是指節點所表示的 SharePoint 元件。 如需示範如何執行這項操作的逐步解說，請參閱[逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   顯示自訂的讀取/寫入資料的屬性。 程式碼範例示範如何執行這項操作，請參閱[How to:擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## <a name="get-data-for-built-in-nodes"></a>取得內建的節點中的資料
 所有 Visual Studio 所提供的內建節點包含它們所代表的 SharePoint 元件相關的一些資料。 比方說，表示 SharePoint 網站上的清單的節點會提供有關清單中，例如標題和清單的預設檢視 URL 的一些資料。  
  
 若要存取此資料，擷取中的資料物件<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>物件，表示您感興趣的節點。 資料物件的類型取決於節點的類型。  
  
 下列程式碼範例示範如何取得清單節點中的資料物件。 若要查看這個內容中的較大範例的範例，請參閱[How to:取得伺服器總管 中的內建 SharePoint 節點資料](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 下表列出每個內建的節點類型的資料物件類型。  
  
|節點類型|資料物件類型|  
|---------------|----------------------|  
|SharePoint 網站節點|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|內容類型|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|功能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|欄位|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|清單|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|清單範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|清單檢視 (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|工作流程關聯|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|工作流程範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 如需使用詳細資訊<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性，請參閱 <<c2> [ 相關聯的自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## <a name="see-also"></a>另請參閱
 [逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [如何：擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [如何：伺服器總管 中新增自訂 SharePoint 節點](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [如何：取得伺服器總管 中的內建 SharePoint 節點資料](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [將自訂的資料產生關聯的 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [瀏覽 SharePoint 連線，使用 伺服器總管](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
