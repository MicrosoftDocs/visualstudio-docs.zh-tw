---
title: 如何： 擴充 SharePoint 節點在 伺服器總管 |Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1dee26ae729dedc2d38895ca84e430ffcbad875f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118739"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>如何： 擴充 SharePoint 節點在 伺服器總管
  您可以擴充節點底下**SharePoint 連線**中的節點**伺服器總管**。 當您想要將新的子節點、 快顯功能表項目或屬性新增至現有的節點時，這非常有用。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>若要擴充 SharePoint 節點在 伺服器總管  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面的類別。  
  
4.  新增<xref:System.ComponentModel.Composition.ExportAttribute>屬性加入該類別。 這個屬性可讓 Visual Studio 來探索及載入您<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>屬性建構函式的型別。  
  
5.  新增<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>屬性加入該類別。 這個屬性會指定您想要擴充的節點類型的字串識別碼。  
  
     若要指定 Visual Studio 所提供的內建的節點類型，請將其中一個下列的列舉值傳遞至屬性建構函式：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>： 使用這些值來指定網站連線節點 （節點顯示網站 Url），站台節點或在其他所有的父節點**伺服器總管**。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>： 指定其中一個內建節點代表 SharePoint 網站，例如代表清單、 欄位或內容類型的節點上的個別元件使用這些值。  
  
6.  在您實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>方法，使用成員*nodeType*參數來將功能加入至節點。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>可用來存取事件中所定義的物件<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>介面。 例如，您可以處理下列事件：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>： 處理這個事件來將新的子節點新增至節點。 如需詳細資訊，請參閱 <<c0> [ 如何： 自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>： 處理這個事件來將自訂的捷徑功能表項目新增至節點。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>： 處理這個事件來將自訂屬性新增至節點。 屬性會出現在**屬性**視窗中選取節點時。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立兩種不同的節點延伸模組：  
  
-   延伸模組，將操作功能表項目加入至 SharePoint 網站節點。 當您按一下的功能表項目時，它會顯示已按下的節點名稱。  
  
-   擴充功能，新增一個名為的自訂屬性**ContosoExampleProperty**到每個節點都代表一個名為欄位**主體**。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 此延伸模組會將可編輯的字串屬性加入至節點。 您也可以建立自訂的屬性，顯示從 SharePoint 伺服器的唯讀資料。 如需示範如何執行這項操作的範例，請參閱 <<c0> [ 逐步解說： 擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署**伺服器總管**延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [如何： 自訂 SharePoint 節點加入至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [逐步解說： 擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [將自訂的資料產生關聯的 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
