---
title: 如何：取得 SharePoint 專案服務 |Microsoft Docs
description: 瞭解如何在專案系統延伸模組、伺服器總管擴充功能或其他 Visual Studio 擴充功能中存取 SharePoint 專案服務。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 553b4ae3b7ecfa9fa49065824020ebdcecf77215
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304443"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>如何：取得 SharePoint 專案服務
  您可以使用下列類型的解決方案來存取 SharePoint 專案服務：

- SharePoint 專案系統的延伸模組，例如專案延伸、專案專案延伸或專案專案類型定義。 如需這些擴充功能類型的詳細資訊，請參閱 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

- **伺服器總管** 中 [ **SharePoint 連接**] 節點的延伸。 如需這些擴充功能類型的詳細資訊，請參閱 [伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

- 另一種類型的 Visual Studio 延伸模組，例如 VSPackage。

## <a name="retrieve-the-service-in-project-system-extensions"></a>在專案系統延伸中取出服務
 在 SharePoint 專案系統的任何擴充功能中，您可以使用物件的屬性來存取專案服務 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 。

 您也可以使用下列程式來捕獲專案服務。

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>若要在專案延伸中取得服務

1. 在您的介面實 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> ，找出 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法。

2. 使用 *projectService* 參數來存取服務。

     下列程式碼範例示範如何使用專案服務，將訊息以簡單的專案延伸寫入至 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗。

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     如需建立專案擴充功能的詳細資訊，請參閱 [如何：建立 SharePoint 專案延伸](../sharepoint/how-to-create-a-sharepoint-project-extension.md)模組。

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>若要在專案專案延伸中取得服務

1. 在您的介面實 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> ，找出 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法。

2. 使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> *projectItemType* 參數的屬性來取得服務。

     下列程式碼範例將示範如何使用專案服務，將訊息寫入至 [ **輸出** 視窗] 和 [ **錯誤清單** ] 視窗中的 [ **清單定義** ] 專案專案的簡單延伸。

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     如需建立專案專案擴充功能的詳細資訊，請參閱 [如何：建立 SharePoint 專案專案延伸](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)模組。

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>若要在專案專案類型定義中取出服務

1. 在您的介面實 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> ，找出 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法。

2. 使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> *typeDefinition* 參數的屬性來取得服務。

     下列程式碼範例示範如何使用專案服務，將訊息寫入至簡單專案專案類型定義中的 [ **輸出** 視窗] 和 [ **錯誤清單** ] 視窗。

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     如需定義專案專案類型的詳細資訊，請參閱 [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>在伺服器總管擴充功能中取出服務
 在 **伺服器總管** 的 [ **SharePoint 連接**] 節點擴充功能中，您可以使用物件的屬性來存取專案服務 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 。

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>若要在伺服器總管擴充功能中取出服務

1. <xref:System.IServiceProvider>從您的延伸模組 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 中的物件屬性取得物件 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 。

2. 使用 <xref:System.IServiceProvider.GetService%2A> 方法來要求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件。

     下列程式碼範例示範如何使用專案服務，將訊息從擴充功能新增至 **伺服器總管** 中清單節點的快捷方式功能表，寫入至 [**輸出**] 視窗和 [**錯誤清單**] 視窗。

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     如需在 **伺服器總管** 中擴充 [ **sharepoint 連接**] 節點的詳細資訊，請參閱 [如何：在伺服器總管中擴充 sharepoint 節點](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>取得其他 Visual Studio 延伸模組中的服務
 您可以在 VSPackage 中，或在任何可存取 automation 物件模型中之物件的 Visual Studio 延伸模組中取得專案服務 <xref:EnvDTE80.DTE2> ，例如實介面的專案範本 wizard <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 。

 在 VSPackage 中，您可以 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 使用下列其中一種方法來要求物件：

- <xref:System.IServiceProvider.GetService%2A>衍生自類別之 Managed VSPackage 的方法 <xref:Microsoft.VisualStudio.Shell.Package> 。 如需詳細資訊，請參閱 [如何：取得服務](../extensibility/how-to-get-a-service.md)。

- 靜態 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法。 如需詳細資訊，請參閱 [使用 GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)。

  在可存取物件的 Visual Studio 擴充功能中 <xref:EnvDTE80.DTE2> ，您可以 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 使用物件的方法來要求物件 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:Microsoft.VisualStudio.Shell.ServiceProvider> 。 如需詳細資訊，請參閱 [從 DTE 物件取得服務](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)。

## <a name="see-also"></a>另請參閱
- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [How to：取得服務](../extensibility/how-to-get-a-service.md)
- [如何：搭配專案範本使用嚮導](../extensibility/how-to-use-wizards-with-project-templates.md)
