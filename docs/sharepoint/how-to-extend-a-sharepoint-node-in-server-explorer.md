---
title: 如何：在伺服器總管中擴充 SharePoint 節點 |Microsoft Docs
description: 瞭解如何使用 [SharePoint 連接] 節點，在伺服器總管中擴充 SharePoint 節點。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e38f1d18736c18f5273eb2e202de52af81e73f85
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217446"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>如何：在伺服器總管中擴充 SharePoint 節點
  您可以在 **伺服器總管** 中的 [ **SharePoint 連接**] 節點底下擴充節點。 當您想要將新的子節點、快捷方式功能表項目或屬性加入至現有的節點時，這會很有用。 如需詳細資訊，請參閱 [伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>若要在伺服器總管中擴充 SharePoint 節點

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio SharePoint

    - VisualStudio 延伸模組。

    - System.ComponentModel.Composition

3. 建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面的類別。

4. 將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入該類別。 這個屬性可讓 Visual Studio 探索和載入您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 執行。 將型別傳遞 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 至屬性（attribute）的函式。

5. 將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 屬性加入該類別。 這個屬性會指定您要擴充之節點類型的字串識別碼。

     若要指定 Visual Studio 所提供的內建節點類型，請將下列其中一個列舉值傳遞給屬性函式：

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用這些值來指定網站連接節點 (節點，這些節點會在 **伺服器總管** 中顯示網站 url) 、網站節點或所有其他父節點。

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：使用這些值來指定其中一個內建節點，代表 SharePoint 網站上的個別元件，例如代表清單、欄位或內容類型的節點。

6. 在您的方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> ，請使用 *nodeType* 參數的成員將功能加入至節點。 這個參數是一個 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> 物件，可讓您存取在介面中定義的事件 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> 。 例如，您可以處理下列事件：

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>：處理這個事件，以將新的子節點加入至節點。 如需詳細資訊，請參閱 [如何：將自訂 SharePoint 節點新增至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)。

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>：處理這個事件，以將自訂快捷方式功能表項目加入至節點。

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>：處理此事件，以將自訂屬性加入至節點。 選取節點時，屬性會出現在 [ **屬性** ] 視窗中。

## <a name="example"></a>範例
 下列程式碼範例示範如何建立兩種不同類型的節點擴充：

- 將內容功能表項目加入至 SharePoint 網站節點的延伸模組。 當您按一下功能表項目時，它會顯示已按一下的節點名稱。

- 此延伸模組會將名為 **ContosoExampleProperty** 的自訂屬性新增至代表名為 **Body** 之欄位的每個節點。

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  此延伸模組會將可編輯的字串屬性新增至節點。 您也可以建立自訂屬性，以顯示來自 SharePoint 伺服器的唯讀資料。 如需示範如何執行此動作的範例，請參閱 [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- VisualStudio 延伸模組。

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署 **伺服器總管** 擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的擴充功能。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [如何：將自訂 SharePoint 節點新增至伺服器總管](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [將自訂資料與 SharePoint 工具延伸模組產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
