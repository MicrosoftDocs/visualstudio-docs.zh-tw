---
title: 如何： 擷取 SharePoint 專案服務 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e2dc633621734740065b8e0c80dd34795eac830
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118783"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>如何： 擷取 SharePoint 專案服務
  您可以存取 SharePoint 專案服務，在下列幾種解決方案：  
  
-   SharePoint 專案系統，例如專案延伸模組、 專案項目擴充功能或專案項目類型定義的延伸模組。 如需這些類型的擴充功能的詳細資訊，請參閱[擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   延伸模組**SharePoint 連線**中的節點**伺服器總管**。 如需這些類型的擴充功能的詳細資訊，請參閱[擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
-   另一種 Visual Studio 擴充功能，例如 VSPackage 的詳細資訊。  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>擷取專案系統擴充功能中的服務  
 在 SharePoint 專案系統的任何延伸模組，您可以存取專案服務，利用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件。  
  
 您也可以使用下列程序，以擷取專案服務。  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>若要擷取專案擴充功能中的服務  
  
1.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>介面中，找出<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法。  
  
2.  使用*projectService*參數來存取服務。  
  
     下列程式碼範例示範如何使用專案服務，以將訊息寫入**輸出**視窗和**錯誤清單**簡單專案擴充功能中的視窗。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     如需建立專案擴充功能的詳細資訊，請參閱[如何： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>若要擷取的專案項目延伸模組中的服務  
  
1.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>介面中，找出<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法。  
  
2.  使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>的屬性*projectItemType*參數，以擷取服務。  
  
     下列程式碼範例示範如何使用專案服務，以將訊息寫入**輸出**視窗和**錯誤清單**視窗中的簡單擴充**清單定義**專案項目。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     如需建立專案項目擴充功能的詳細資訊，請參閱 <<c0> [ 如何： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>若要擷取的專案項目類型定義中的服務  
  
1.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面中，找出<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。  
  
2.  使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>的屬性*typeDefinition*參數，以擷取服務。  
  
     下列程式碼範例示範如何使用專案服務，以將訊息寫入**輸出**視窗和**錯誤清單**簡單的專案項目類型定義中的視窗。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     如需有關如何定義專案項目類型的詳細資訊，請參閱 <<c0> [ 如何： 定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>擷取在伺服器總管延伸模組中的服務  
 中的延伸模組**SharePoint 連線**中的節點**伺服器總管**，您可以使用，以存取專案服務<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>物件。  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>若要擷取的伺服器總管延伸模組中的服務  
  
1.  取得<xref:System.IServiceProvider>物件從<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>延伸模組中的物件。  
  
2.  使用<xref:System.IServiceProvider.GetService%2A>方法來要求<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件。  
  
     下列程式碼範例示範如何使用專案服務，以將訊息寫入**輸出**視窗和**錯誤清單**從延伸模組新增到清單節點中快顯功能表視窗**伺服器總管**。  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     如需有關擴充**SharePoint 連線**中的節點**伺服器總管**，請參閱[如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>擷取其他 Visual Studio 擴充功能中的服務  
 您可以擷取專案服務在 VSPackage 中，或可存取任何 Visual Studio 擴充功能<xref:EnvDTE80.DTE2>自動化物件模型，例如實作專案範本精靈 中的物件<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面。  
  
 在 VSPackage 中，您可以要求<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件使用下列方法之一：  
  
-   <xref:System.IServiceProvider.GetService%2A>方法的 managed VSPackage，衍生自<xref:Microsoft.VisualStudio.Shell.Package>類別。 如需詳細資訊，請參閱 <<c0> [ 如何： 取得服務](../extensibility/how-to-get-a-service.md)。  
  
-   靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。 如需詳細資訊，請參閱 <<c0> [ 使用 GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)。  
  
 在 Visual Studio 擴充功能具有存取權<xref:EnvDTE80.DTE2>物件，您可以要求<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>使用的物件<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>方法<xref:Microsoft.VisualStudio.Shell.ServiceProvider>物件。 如需詳細資訊，請參閱 <<c0> [ 從 DTE 物件取得服務](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)。  
  
## <a name="see-also"></a>另請參閱
 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)   
 [如何： 取得服務](../extensibility/how-to-get-a-service.md)   
 [如何： 搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
