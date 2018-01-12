---
title: "如何： 擴充 SharePoint 節點在 [伺服器總管] |Microsoft 文件"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d6fd079980897085f4e9c17a16dc57279ec586c2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>如何：在伺服器總管中擴充 SharePoint 節點
  您可以擴充節點下的**SharePoint 連接**節點**伺服器總管**。 當您想要將新的子節點、 快顯功能表項目或屬性加入至現有的節點時，這非常有用。 如需詳細資訊，請參閱[擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>若要擴充 SharePoint 節點在 伺服器總管  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面的類別。  
  
4.  新增<xref:System.ComponentModel.Composition.ExportAttribute>屬性加入該類別。 這個屬性可讓 Visual Studio 來探索和載入您<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>屬性建構函式的類型。  
  
5.  新增<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>屬性加入該類別。 這個屬性會指定您想要擴充的節點類型的字串識別項。  
  
     若要指定 Visual Studio 所提供的內建的節點型別，請將下列的列舉值的其中一個傳遞至屬性建構函式：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>： 使用這些值，指定站台連線節點 （節點顯示的網站 Url），站台的節點或在其他所有的父節點**伺服器總管**。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>： 若要指定其中一個內建節點表示 SharePoint 網站，例如清單、 欄位或內容類型表示的節點上的個別元件使用這些值。  
  
6.  在您實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>方法，使用成員*nodeType*將功能加入節點參數。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>物件，提供存取權中定義的事件<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>介面。 例如，您可以處理下列事件：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>： 處理這個事件來加入新的子節點的節點。 如需詳細資訊，請參閱[How to： 自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>： 處理這個事件以自訂捷徑功能表項目新增至節點。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>： 處理這個事件來將自訂屬性加入至節點。 屬性會出現在**屬性**視窗選取節點時。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立兩個不同類型節點的擴充功能：  
  
-   擴充功能，將操作功能表項目加入至 SharePoint 網站節點。 當您按一下功能表項目時，它會顯示已按下的節點名稱。  
  
-   加入名為的自訂屬性的擴充功能**ContosoExampleProperty**代表名為的欄位每個節點**主體**。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 這項擴充功能可以讓您編輯字串將屬性加入至節點。 您也可以建立顯示唯讀資料，從 SharePoint 伺服器的自訂屬性。 如需示範如何執行這項操作的範例，請參閱[逐步解說： 擴充伺服器總管 來顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署**伺服器總管**延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [逐步解說： 擴充伺服器總管 以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [讓自訂資料與 SharePoint 工具延伸模組產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  