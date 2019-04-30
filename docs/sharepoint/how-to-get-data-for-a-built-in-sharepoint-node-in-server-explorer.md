---
title: HOW TO：取得伺服器總管 中的內建 SharePoint 節點的資料 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1e3ec8fd6598573a60f852727397d6baa63d3e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813732"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>HOW TO：取得伺服器總管 中的內建 SharePoint 節點資料
  在每個內建 SharePoint 節點**伺服器總管**，您可以取得資料為基礎的 SharePoint 元件節點所表示。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

## <a name="example"></a>範例
 下列程式碼範例示範如何取得資料為基礎的 SharePoint 清單的清單節點表示**伺服器總管**。 根據預設，清單中的節點具有**瀏覽器中的檢視**操作功能表項目，您可以按一下以開啟網頁瀏覽器中的清單。 此範例中加入擴充節點清單**在 Visual Studio 中的檢視**直接在 Visual Studio 中開啟清單的內容功能表項目。 程式碼存取的節點，以取得要在 Visual Studio 中開啟清單的 URL 清單資料。

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 此範例會使用 SharePoint 專案服務來取得<xref:EnvDTE.DTE>列出在 Visual Studio 中的物件，用來開啟。 如需有關 SharePoint 專案服務的詳細資訊，請參閱 <<c0> [ 使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

 如需有關建立 SharePoint 節點的擴充功能的基本工作的詳細資訊，請參閱[How to:擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列組件：

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署擴充功能
 若要部署**伺服器總管**延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [如何：擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
