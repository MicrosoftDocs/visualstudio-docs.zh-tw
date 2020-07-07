---
title: 如何：將自訂 SharePoint 節點加入至伺服器總管 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26a2ea6a7ccbfcc80275b55f9230f1a3152ab545
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017046"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>如何：將自訂 SharePoint 節點加入至伺服器總管
  您可以在**伺服器總管**的 [ **SharePoint 連接**] 節點下加入自訂節點。 當您想要顯示預設不會顯示在**伺服器總管**中的其他 SharePoint 元件時，這會很有用。 如需詳細資訊，請參閱[伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

 若要新增自訂節點，請先建立一個定義新節點的類別。 然後建立擴充功能，將節點新增為現有節點的子系。

### <a name="to-define-the-new-node"></a>若要定義新的節點

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio. SharePoint

    - VisualStudio. SharePoint. Explorer 副檔名

    - System.ComponentModel.Composition

    - System.Drawing

3. 建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面的類別。

4. 將下列屬性新增至類別：

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 探索及載入您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 執行。 將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 類型傳遞給屬性的函式。

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. 在節點定義中，這個屬性會指定新節點的字串識別碼。 建議您使用 [*公司名稱*] 格式。*節點名稱*，確保所有節點都有唯一的識別碼。

5. 在方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> ，請使用*typeDefinition*參數的成員來設定新節點的行為。 這個參數是 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> 物件，可讓您存取介面中定義的事件 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> 。

     下列程式碼範例示範如何定義新的節點。 這個範例假設您的專案包含名為 CustomChildNodeIcon 的圖示做為內嵌資源。

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>若要加入新的節點做為現有節點的子系

1. 在與您的節點定義相同的專案中，建立一個可實作為介面的類別 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 。

2. 將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入該類別。 這個屬性可讓 Visual Studio 探索及載入您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 執行。 將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 類型傳遞給屬性的函式。

3. 將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 屬性加入該類別。 在節點延伸中，這個屬性會指定您要擴充之節點類型的字串識別碼。

     若要指定 Visual Studio 所提供的內建節點類型，請將下列其中一個列舉值傳遞給屬性的函式：

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用這些值來指定網站連線節點（顯示網站 Url 的節點）、網站節點，或**伺服器總管**中的所有其他父節點。

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：使用這些值來指定其中一個內建節點，代表 SharePoint 網站上的個別元件，例如代表清單、欄位或內容類型的節點。

4. 在您的方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> ，處理 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 參數的事件 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> 。

5. 在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 事件處理常式中，將新的節點加入至 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> 事件引數參數所公開之物件的子節點集合。

     下列程式碼範例示範如何在**伺服器總管**中，將新的節點加入為 SharePoint 網站節點的子系。

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>完整範例
 下列程式碼範例提供完整的程式碼，以定義簡單的節點，並將它加入為**伺服器總管**中 SharePoint 網站節點的子系。

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>編譯程式碼
 這個範例假設您的專案包含名為 CustomChildNodeIcon 的圖示做為內嵌資源。 這個範例也需要參考下列元件：

- VisualStudio. SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署**伺服器總管**延伸模組，請 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件建立擴充功能（VSIX）封裝，以及您想要與延伸模組一起散發的任何其他檔案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [在伺服器總管中擴充 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
