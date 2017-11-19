---
title: "如何： 建立 SharePoint 專案擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 04/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21b7291b23376f95e9c0d70a43e6bb69cd29a2d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>如何：建立 SharePoint 專案擴充功能
  當您想要將功能加入至已在 Visual Studio 中開啟任何 SharePoint 專案建立專案擴充功能。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。  

### <a name="to-create-a-project-extension"></a>若要建立專案擴充功能  

1.  建立類別庫 (Class Library) 專案。  

2.  加入下列組件的參考：  

    -   Microsoft.VisualStudio.SharePoint  

    -   System.ComponentModel.Composition  

3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面的類別。  

4.  新增<xref:System.ComponentModel.Composition.ExportAttribute>至類別。 這個屬性可讓 Visual Studio 來探索和載入您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>屬性建構函式的類型。  

5.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法，使用成員*projectService*參數來定義您的擴充功能的行為。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件，提供存取權中定義的事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>介面。  

## <a name="example"></a>範例  
 下列程式碼範例示範如何建立簡單的專案擴充功能，會處理大部分的 SharePoint 專案事件所定義的<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>介面。 若要測試的程式碼，建立 SharePoint 專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]並再將更多專案加入方案、 變更專案屬性的值，或刪除或排除專案。 延伸模組會通知您的事件寫入訊息至**輸出**視窗和**錯誤清單**視窗。  

  ```vb  
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace  
    ```  

    ```csharp  
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }  
  ```  

此範例會使用 SharePoint 專案服務寫入至訊息**輸出**視窗和**錯誤清單**視窗。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  

 如需範例示範如何處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件，請參閱[How to： 將捷徑功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)和[How to： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  

## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  

-   Microsoft.VisualStudio.SharePoint  

-   System.ComponentModel.Composition  

## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  

## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)   
 [如何： 將捷徑功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [如何： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [逐步解說：建立 SharePoint 專案延伸模組](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
