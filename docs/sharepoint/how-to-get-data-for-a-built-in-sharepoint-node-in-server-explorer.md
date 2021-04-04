---
title: 在伺服器總管中取得內建 SharePoint 節點的資料
titleSuffix: ''
description: 在 Visual Studio 的伺服器總管視窗中，取得內建 SharePoint 節點基礎 SharePoint 元件的資料。
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
ms.openlocfilehash: c58de345400c7b724a755839cb8baa1afc3cfce2
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217186"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>如何：在伺服器總管中取得內建 SharePoint 節點的資料
  針對 **伺服器總管** 中的每個內建 sharepoint 節點，您可以取得節點所代表之基礎 sharepoint 元件的資料。 如需詳細資訊，請參閱 [伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

## <a name="example"></a>範例
 下列程式碼範例示範如何取得清單節點在 **伺服器總管** 中所代表基礎 SharePoint 清單的資料。 依預設，[清單] 節點具有 **瀏覽器** 內容功能表項目中的 [View]，您可以按一下以在網頁瀏覽器中開啟清單。 這個範例會 **在 Visual Studio** 內容功能表項目中加入一個可直接在 Visual Studio 中開啟清單的視圖，以擴充清單節點。 程式碼會存取節點的清單資料，以取得要在 Visual Studio 中開啟的清單 URL。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet10":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet10":::

 這個範例會使用 SharePoint 專案服務來取得 <xref:EnvDTE.DTE> 用來在 Visual Studio 中開啟清單的物件。 如需有關 SharePoint 專案服務的詳細資訊，請參閱 [使用 sharepoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

 如需建立 SharePoint 節點擴充功能之基本工作的詳細資訊，請參閱 [如何：在伺服器總管中擴充 sharepoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- EnvDTE

- VisualStudio SharePoint

- VisualStudio 延伸模組。

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署 **伺服器總管** 擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的擴充功能。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [在 Visual Studio 中部署 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
