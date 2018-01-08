---
title: "如何： 建立 SharePoint 專案項目擴充功能 |Microsoft 文件"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b927b71e33ab6a26729a2db9190e2755eee092a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>如何：建立 SharePoint 專案項目擴充功能
  當您想要將功能加入至已安裝 Visual Studio 中的 SharePoint 專案項目時，請建立專案項目擴充功能。 如需詳細資訊，請參閱[擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。  
  
### <a name="to-create-a-project-item-extension"></a>若要建立專案項目擴充功能  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面的類別。  
  
4.  類別中加入下列屬性：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 來探索和載入您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>屬性建構函式的類型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 中的專案項目延伸模組，這個屬性會識別您想要擴充的專案項目。 將專案項目識別碼傳遞給屬性建構函式。 如需隨附於 Visual Studio 的專案項目識別碼的清單，請參閱[擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。  
  
5.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法，使用成員*projectItemType*參數來定義您的擴充功能的行為。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>物件，提供存取權中定義的事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>介面。 若要存取所擴充的專案項目類型的特定執行個體，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>事件，例如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立簡單的擴充功能事件接收器專案項目。 每次使用者加入事件接收器專案項目加入 SharePoint 專案時，此延伸模組會將訊息寫入**輸出**視窗和**錯誤清單**視窗。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 此範例會使用 SharePoint 專案服務寫入至訊息**輸出**視窗和**錯誤清單**視窗。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  