---
title: 如何： 將捷徑功能表項目新增至 SharePoint 專案項目擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a3e92d3131fb52342eb2d5ee10abd13a9dd005e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756041"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>如何： 將捷徑功能表項目新增至 SharePoint 專案項目擴充功能
  您可以透過專案項目擴充功能，將快顯功能表項目新增至現有的 SharePoint 專案項目中。 使用者以滑鼠右鍵按一下專案項目中的時，會出現的功能表項目**方案總管 中**。  
  
 下列步驟假設您已建立的專案項目延伸模組。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>若要加入專案項目擴充功能中的捷徑功能表項目  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件*projectItemType*參數。  
  
2.  在您的事件處理常式，如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件，加入新<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>物件<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>或<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>事件引數參數的集合。  
  
3.  在 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>新的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>物件中，執行您想要在使用者按一下您的快顯功能表項目時執行的工作。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將捷徑功能表項目加入至事件接收器的專案項目。 當使用者按一下滑鼠右鍵中的專案項目**方案總管**，然後按一下**將訊息寫入至輸出視窗**功能表項目，Visual Studio 會顯示在訊息**輸出**視窗。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 此範例會使用 SharePoint 專案服務來將訊息寫入**輸出**視窗。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件的類別庫專案：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [如何： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何： 將屬性加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [逐步解說： 擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
