---
title: SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換 |Microsoft 文件
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
ms.openlocfilehash: d91b7d3927b9723c943676cf3ce15c4bc808b906
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692115"
---
# <a name="converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換
  在某些情況下您可能會有物件 SharePoint 專案系統中，而且您想要使用 Visual Studio 自動化物件模型或整合物件模型中對應物件的功能，反之亦然。 在這些情況下，您可以使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>SharePoint 專案服務，將物件轉換成不同的物件模型的方法。  
  
 例如，您可能會有<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件，但您想要使用方法只可用在<xref:EnvDTE.Project>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>物件。 在此情況下，您可以使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>方法，將轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>至<xref:EnvDTE.Project>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>。  
  
 如需 Visual Studio 自動化物件模型和 Visual Studio integration 物件模型的詳細資訊，請參閱[程式設計模型的 SharePoint 工具擴充功能的概觀](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## <a name="types-of-conversions"></a>類型的轉換
 下表列出這個方法可以 SharePoint 專案系統和其他 Visual Studio 物件模型之間進行轉換的類型。  
  
|SharePoint 專案系統類型|自動化和整合物件模型中對應的型別|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 或<br /><br /> 在 Visual Studio 整合物件模型專案的基礎 COM 物件所實作的任何介面。 這些介面包括<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> （或衍生的介面），和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。 由專案的主要介面的清單，請參閱[專案模型的核心元件](/visualstudio/extensibility/internals/project-model-core-components)。|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 或<br /><br /> A<xref:System.UInt32> （也稱為 VSITEMID） 的值，識別中的專案成員<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>包含它。 此值可以傳遞至*itemid*一些參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>方法。|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>方法，將轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件<xref:EnvDTE.Project>。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 這個範例需要：  
  
-   SharePoint 專案系統具有 EnvDTE.dll 組件的參考延伸模組。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   暫存器的程式碼`projectService_ProjectAdded`方法以處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件。 如需範例，請參閱[How to： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## <a name="see-also"></a>另請參閱
 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)   
 [如何： 擷取 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [SharePoint 工具延伸模組的程式撰寫模型概觀](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
