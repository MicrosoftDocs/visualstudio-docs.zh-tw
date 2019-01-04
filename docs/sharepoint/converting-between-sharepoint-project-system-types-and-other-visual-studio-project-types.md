---
title: SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換 |Microsoft Docs
ms.date: 02/02/2017
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
ms.openlocfilehash: 145f080812356a4387401ef47adbd48fe783e60b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920614"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換
  在某些情況下您可能會有一個物件，在 SharePoint 專案系統，而且想要使用 Visual Studio 自動化物件模型或整合物件模型中對應物件的功能，反之亦然。 在這些情況下，您可以使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>SharePoint 專案服務，將物件轉換成不同的物件模型的方法。

 例如，您可能會有<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件，但您想要使用，則只能在方法<xref:EnvDTE.Project>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>物件。 在此情況下，您可以使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>方法，將轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>要<xref:EnvDTE.Project>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>。

 如需有關 Visual Studio 自動化物件模型和 Visual Studio integration 物件模型的詳細資訊，請參閱 <<c0> [ 概觀的程式設計模型的 SharePoint 工具擴充功能](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。

## <a name="types-of-conversions"></a>類型的轉換
 下表列出這個方法可以將 SharePoint 專案系統與其他 Visual Studio 物件模型之間的轉換類型。

|SharePoint 專案系統類型|自動化和整合物件模型中對應的型別|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 或<br /><br /> 在 Visual Studio integration 物件模型專案的基礎 COM 物件實作任何介面。 這些介面包括<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> （或衍生的介面），和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。 如需主要專案所實作的介面，請參閱[專案模型的核心元件](../extensibility/internals/project-model-core-components.md)。|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 或<br /><br /> A<xref:System.UInt32> （也稱為 VSITEMID） 值，這個值會識別中的專案成員<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>包含它。 此值可以傳遞給*itemid*參數的一些<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>方法。|

## <a name="example"></a>範例
 下列程式碼範例示範如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>方法，將轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件到<xref:EnvDTE.Project>。

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 這個範例需要：

-   具有參考 SharePoint 專案系統的延伸模組*EnvDTE.dll*組件。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

-   程式碼來註冊`projectService_ProjectAdded`方法以處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>事件的<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件。 如需範例，請參閱[How to:建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。

## <a name="see-also"></a>另請參閱

- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [如何：擷取 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [概觀的程式設計模型的 SharePoint 工具擴充功能](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
