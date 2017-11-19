---
title: "如何： 取得伺服器總管 中的內建 SharePoint 節點資料 |Microsoft 文件"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b61003516d7551c99f6e265ca2eeced9226958df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>如何：取得伺服器總管的內建 SharePoint 節點資料
  在每個內建 SharePoint 節點**伺服器總管**，取得基礎 SharePoint 元件，則節點代表的資料。 如需詳細資訊，請參閱[擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何取得資料為基礎的 SharePoint 清單的清單節點表示**伺服器總管**。 根據預設，清單中的節點具有**瀏覽器中的檢視**操作功能表項目，您可以按一下來開啟網頁瀏覽器中的清單。 這個範例藉由加入擴充清單節點**Visual Studio 中的檢視**直接在 Visual Studio 中開啟清單的內容功能表項目。 程式碼存取的節點，以取得要在 Visual Studio 中開啟清單的 URL 清單資料。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 這個範例會使用 SharePoint 專案服務來取得<xref:EnvDTE.DTE>列出 Visual Studio 中的物件，用來開啟。 如需 SharePoint 專案服務的詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 如需建立 SharePoint 節點的擴充功能的基本工作的詳細資訊，請參閱[如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署**伺服器總管**延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)   
 [部署 Visual Studio 中 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  