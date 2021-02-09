---
title: 如何：建立 SharePoint 專案延伸模組 |Microsoft Docs
description: 瞭解如何建立專案延伸，讓您可以將功能加入至 Visual Studio 中開啟的任何 SharePoint 專案。
ms.custom: SEO-VS-2020
ms.date: 04/28/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88d2a7b411097bdf2a90ec04456bfc4419e31c30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923337"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>如何：建立 SharePoint 專案延伸模組
  當您想要將功能加入至 Visual Studio 中開啟的任何 SharePoint 專案時，請建立專案延伸模組。 如需詳細資訊，請參閱 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

### <a name="to-create-a-project-extension"></a>若要建立專案延伸模組

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio SharePoint

    - System.ComponentModel.Composition

3. 建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面的類別。

4. 將加入 <xref:System.ComponentModel.Composition.ExportAttribute> 至類別。 這個屬性可讓 Visual Studio 探索和載入您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 執行。 將型別傳遞 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 至屬性（attribute）的函式。

5. 在方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> ，請使用 *projectService* 參數的成員定義您的延伸模組行為。 這個參數是一個 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件，可讓您存取在介面中定義的事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 。

## <a name="example"></a>範例
 下列程式碼範例示範如何建立簡單的專案擴充功能，以處理介面所定義的大部分 SharePoint 專案事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 。 若要測試程式碼，請在中建立 SharePoint 專案， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 然後將更多專案加入至方案、變更專案屬性值，或刪除或排除專案。 延伸模組會將訊息寫入至 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗，以通知您事件。

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

這個範例會使用 SharePoint 專案服務，將訊息寫入 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗。 如需詳細資訊，請參閱 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

 如需示範如何處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 和事件的範例 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> ，請參閱 [如何：將快捷方式功能表項目加入至 Sharepoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) 和 [如何：將屬性加入至 sharepoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [如何：將快捷方式功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [逐步解說：建立 SharePoint 專案延伸模組](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
