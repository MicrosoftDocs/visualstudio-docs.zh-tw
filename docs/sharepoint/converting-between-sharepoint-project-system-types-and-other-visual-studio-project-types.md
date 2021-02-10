---
title: 轉換： SharePoint 專案系統類型與其他類型之間的轉換
titleSuffix: ''
description: 在 SharePoint 專案系統類型與其他 Visual Studio 專案類型之間進行轉換。 查看詳述可轉換之類型的清單。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc0eca8005c4eee6e1eb89c410b50be5d0228ec6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946328"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>在 SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換
  在某些情況下，您的 SharePoint 專案系統中可能會有一個物件，而您想要使用 Visual Studio automation 物件模型或整合物件模型中對應物件的功能，反之亦然。 在這些情況下，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> SharePoint 專案服務的方法，將物件轉換為不同的物件模型。

 例如，您可能會有 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件，但您想要使用僅適用于 <xref:EnvDTE.Project> 或物件的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 。 在此情況下，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法將轉換成 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 。

 如需 Visual Studio automation 物件模型和 Visual Studio 整合物件模型的詳細資訊，請參閱 [SharePoint 工具擴充功能的程式設計模型總覽](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。

## <a name="types-of-conversions"></a>轉換類型
 下表列出這個方法可以在 SharePoint 專案系統和其他 Visual Studio 物件模型之間轉換的類型。

|SharePoint 專案系統類型|Automation 和 integration 物件模型中的對應類型|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 或<br /><br /> Visual Studio 整合物件模型中，由專案的基礎 COM 物件所執行的任何介面。 這些介面包括 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (或衍生介面) 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 。 如需專案所執行的主要介面清單，請參閱 [專案模型核心元件](../extensibility/internals/project-model-core-components.md)。|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 或<br /><br /> <xref:System.UInt32>值 (也稱為 VSITEMID) ，可在中識別包含該專案的專案成員 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 。 這個值可以傳遞給某些方法的 *itemid* 參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 。|

## <a name="example"></a>範例
 下列程式碼範例將示範如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法，將物件轉換 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 為 <xref:EnvDTE.Project> 。

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 這個範例需要：

- 具有 *EnvDTE.dll* 元件之參考的 SharePoint 專案系統延伸模組。 如需詳細資訊，請參閱 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

- 註冊 `projectService_ProjectAdded` 方法以處理物件事件的程式碼 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 。 如需範例，請參閱 [如何：建立 SharePoint 專案延伸](../sharepoint/how-to-create-a-sharepoint-project-extension.md)模組。

## <a name="see-also"></a>另請參閱

- [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)
- [如何：取得 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint 工具擴充功能的程式設計模型總覽](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
