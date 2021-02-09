---
title: 擴充伺服器總管中的 [SharePoint 連接] 節點 |Microsoft Docs
titleSuffix: ''
description: 在 Visual Studio 的 [伺服器總管] 視窗中，展開 [SharePoint 連接] 節點。 將自訂屬性新增至節點。 取得內建節點的資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c10c2bc69086e3c98633ba746c1e6fc8d7f2a20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889690"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>擴充伺服器總管中的 [SharePoint 連接] 節點
  在 Visual Studio 中，您可以使用 [**伺服器總管**] 視窗中的 [ **SharePoint 連接**] 節點連接到開發電腦上的本機 SharePoint 網站。 此節點會以階層式樹狀檢視顯示本機 SharePoint 網站的許多元件。 例如，您可以在本機網站上查看清單、文件庫和內容類型。 如需使用 **伺服器總管** 連接到本機 SharePoint 網站的詳細資訊，請參閱 [使用伺服器總管流覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)。

 您可以藉由建立現有節點的延伸模組，或建立自訂節點類型，並將它加入至節點階層中，來擴充 [ **SharePoint 連接** ] 節點。

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>擴充 SharePoint 連接節點的工作
 若要擴充現有的節點，請建立可執行介面的 Visual Studio 延伸模組 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 。 當您擴充節點時，可以將功能加入至節點，例如您自己的快捷方式功能表項目或自訂屬性。 如需詳細資訊，請參閱 [如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。

 若要建立自訂節點類型，請建立可執行介面的 Visual Studio 延伸模組 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 。 如果您想要顯示預設不會顯示在 **伺服器總管** 中的 SharePoint 網站元件，請建立自訂節點。 例如， **伺服器總管** 預設不會顯示 SharePoint 網站的 Web 元件庫，但您可以加入執行這項工作的自訂節點。 如需詳細資訊，請參閱 [如何：將自訂 SharePoint 節點加入伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) 和 [逐步解說：擴充伺服器總管以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。

## <a name="add-custom-properties-to-nodes"></a>將自訂屬性新增至節點
 當您擴充節點或建立自訂節點類型時，可以將自訂屬性加入至節點。 選取節點時，屬性會出現在 [ **屬性** ] 視窗中。

 您可以將兩種類型的自訂屬性新增至節點：

- 顯示來自 SharePoint 網站的一組唯讀資料的屬性。 資料描述節點所代表的 SharePoint 元件。 如需示範如何執行此作業的逐步解說，請參閱 [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。

- 顯示自訂讀取/寫入資料的屬性。 如需示範如何執行這項作業的程式碼範例，請參閱 [如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。

## <a name="get-data-for-built-in-nodes"></a>取得內建節點的資料
 Visual Studio 所提供的所有內建節點，都包含有關其所代表之 SharePoint 元件的一些資料。 例如，代表 SharePoint 網站上清單的節點會提供有關清單的一些資料，例如清單的預設視圖的標題和 URL。

 若要存取此資料，請從 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 代表您感興趣之節點的物件屬性中取出資料物件。 資料物件的型別取決於節點的型別。

 下列程式碼範例示範如何取得清單節點的資料物件。 若要在較大範例的內容中查看這個範例，請參閱 [如何：在伺服器總管中取得內建 SharePoint 節點的資料](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)。

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 下表列出每個內建節點類型的資料物件類型。

|節點類型|資料物件類型|
|---------------|----------------------|
|SharePoint 網站節點|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|內容類型|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|功能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|欄位|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|清單範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|>microsoft.sharepoint.spview) 的清單視圖 (|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|工作流程關聯|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|工作流程範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 如需使用屬性的詳細資訊 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> ，請參閱 [將自訂資料與 SharePoint 工具延伸](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)模組產生關聯。

## <a name="see-also"></a>另請參閱
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [如何：將自訂 SharePoint 節點新增至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [如何：在伺服器總管中取得內建 SharePoint 節點的資料](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [將自訂資料與 SharePoint 工具延伸模組產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [使用伺服器總管流覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
