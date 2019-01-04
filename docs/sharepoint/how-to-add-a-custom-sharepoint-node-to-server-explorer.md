---
title: HOW TO：自訂 SharePoint 節點加入至伺服器總管 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bc648abd1d8981bd5c64782bd094e40d507b4142
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937659"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>HOW TO：伺服器總管 中新增自訂 SharePoint 節點
  您可以新增自訂節點底下**SharePoint 連線**中的節點**伺服器總管**。 當您想要顯示其他 SharePoint 元件，不會顯示在此方法**伺服器總管**預設。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
 若要新增自訂的節點，請先建立一個類別來定義新的節點。 然後建立了延伸模組，將節點加入現有的節點的子系。  
  
### <a name="to-define-the-new-node"></a>若要定義新的節點  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面的類別。  
  
4.  將下列屬性新增至類別：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 來探索及載入您<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>屬性建構函式的型別。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. 在節點定義中，這個屬性會指定新節點的字串識別碼。 我們建議您使用的格式*公司名稱*。*節點名稱*以確定所有節點都有唯一的識別碼。  
  
5.  在您實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>方法，使用成員*typeDefinition*參數來設定新節點的行為。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>可用來存取事件中所定義的物件<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>介面。  
  
     下列程式碼範例示範如何定義新的節點。 這個範例假設您的專案包含名為 CustomChildNodeIcon 做為內嵌資源的圖示。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>若要將新節點新增為現有節點的子系  
  
1.  在您的節點定義相同的專案，建立可實作類別<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>介面。  
  
2.  將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入該類別。 這個屬性可讓 Visual Studio 來探索及載入您<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>屬性建構函式的型別。  
  
3.  將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 屬性加入該類別。 在節點的擴充功能，這個屬性會指定您想要擴充的節點類型的字串識別碼。  
  
     若要指定 Visual Studio 所提供的內建的節點類型，請將其中一個下列的列舉值傳遞至屬性建構函式：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用這些值來指定網站連線節點 （節點顯示網站 Url），站台節點或在其他所有父節點**伺服器總管**。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：您可以使用這些值來指定其中一個內建節點代表 SharePoint 網站，例如代表清單、 欄位或內容類型的節點上的個別元件。  
  
4.  在您實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>方法，控制代碼<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>事件的<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>參數。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>事件處理常式，將新節點新增至的子節點集合<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A>事件引數參數所公開的物件。  
  
     下列程式碼範例示範如何將新節點新增為在 SharePoint 網站節點的子系**伺服器總管**。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>完整範例
 下列程式碼範例提供完整的程式碼定義簡單的節點，並將其新增為子系中的 SharePoint 網站節點**伺服器總管**。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例假設您的專案包含名為 CustomChildNodeIcon 做為內嵌資源的圖示。 這個範例也會需要下列組件的參考：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署**伺服器總管**延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署擴充功能的 Visual Studio 中 SharePoint 工具](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [如何：擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
