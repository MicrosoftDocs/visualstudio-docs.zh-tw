---
title: 如何： 將捷徑功能表項目加入至 SharePoint 專案 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aea2dd600548d76d57d58c8cfc0313c92ccb9f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>如何：將捷徑功能表項目加入至 SharePoint 專案
  您可以加入任何 SharePoint 專案的捷徑功能表項目。 當使用者以滑鼠右鍵按一下專案節點中的，會出現的功能表項目**方案總管 中**。  
  
 下列步驟假設您已經建立專案擴充功能。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>若要加入至 SharePoint 專案的捷徑功能表項目  
  
1.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>事件*projectService*參數。  
  
2.  在您的事件處理常式，如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>事件，加入新<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>物件<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A>或<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A>事件引數參數的集合。  
  
3.  在<xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>針對新的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>物件，請執行您想要在使用者按一下您的快顯功能表項目時執行的工作。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將捷徑功能表項目加入至 SharePoint 專案節點中**方案總管 中**。 當使用者以滑鼠右鍵按一下專案節點，並按一下**將訊息寫入至輸出視窗**功能表項目，Visual Studio 會顯示在訊息**輸出**視窗。 這個範例會使用 SharePoint 專案服務，來顯示訊息。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件的類別庫專案：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)   
 [如何： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [如何：將屬性新增至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  