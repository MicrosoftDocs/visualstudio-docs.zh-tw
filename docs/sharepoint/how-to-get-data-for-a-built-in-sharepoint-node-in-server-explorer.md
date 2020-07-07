---
title: 在伺服器總管中取得內建 SharePoint 節點的資料
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bb69773bf3f031b75d63ebe8cb1f1b4a00286c9
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014896"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>如何：在伺服器總管中取得內建 SharePoint 節點的資料
  針對**伺服器總管**中的每個內建 sharepoint 節點，您可以取得節點所代表之基礎 SharePoint 元件的資料。 如需詳細資訊，請參閱[伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

## <a name="example"></a>範例
 下列程式碼範例示範如何取得**伺服器總管**中清單節點所代表之基礎 SharePoint 清單的資料。 根據預設，[清單] 節點**在瀏覽器**內容功能表項目中會有一個 View，您可以按一下此專案，以在網頁瀏覽器中開啟清單。 這個範例會藉由在 Visual Studio 中直接開啟清單的 Visual Studio 快顯功能表專案**中加入視圖**來擴充清單節點。 此程式碼會存取節點的清單資料，以取得要在 Visual Studio 中開啟的清單 URL。

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 這個範例會使用 SharePoint 專案服務來取得 <xref:EnvDTE.DTE> 用來在 Visual Studio 中開啟清單的物件。 如需 SharePoint 專案服務的詳細資訊，請參閱[使用 sharepoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

 如需建立 SharePoint 節點擴充功能之基本工作的詳細資訊，請參閱[如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列元件：

- EnvDTE

- VisualStudio. SharePoint

- VisualStudio. SharePoint. Explorer 副檔名

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署**伺服器總管**延伸模組，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件建立擴充功能（VSIX）封裝，以及您想要與延伸模組一起散發的任何其他檔案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [在伺服器總管中擴充 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [如何：在伺服器總管中擴充 SharePoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [在 Visual Studio 中部署 SharePoint 工具的擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
