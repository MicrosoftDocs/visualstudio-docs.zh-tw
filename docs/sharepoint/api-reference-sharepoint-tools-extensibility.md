---
title: " (SharePoint 工具擴充性) 的 API 參考 |Microsoft Docs"
description: 請參閱 Visual Studio 中擴充 SharePoint 工具的 API 參考檔。 查看相關命名空間的清單，例如 VisualStudio。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec07272ede6c957afb43c29342e8479e67d1dd0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851713"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a> (SharePoint 工具擴充性) 的 API 參考
  本章節包含在 Visual Studio 中擴充 SharePoint 工具的 API 參考檔。

## <a name="in-this-section"></a>本節內容
 <xref:Microsoft.VisualStudio.SharePoint>

 包含用來擴充 SharePoint 專案系統的類型。 例如，您可以擴充內建的 SharePoint 專案和專案項目，或您可以建立您自己的專案項目。

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 包含您可以用來建立自訂 *SharePoint 命令* 的類型。 SharePoint 命令是從 SharePoint 工具擴充功能呼叫 SharePoint 伺服器物件模型的方法。

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 包含用來擴充 SharePoint 專案部署程式的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 包含用來在 **伺服器總管** 中擴充 SharePoint 節點或定義您自己的節點類型的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 包含類型，可讓您用來取得內建 **伺服器總管** 節點的相關資訊，這些節點代表 SharePoint 網站上的個別元件，例如代表清單、欄位或內容類型的節點。

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 包含用來存取 SharePoint 專案中功能定義的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 包含用來存取 SharePoint 專案中封裝定義的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 包含用來驗證部署至遠端 SharePoint 網站的 SharePoint 相關應用程式及進行通訊的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 包含用來建立 SharePoint 遠端命令的類型，這些類型會搭配部署至遠端 SharePoint 網站的 SharePoint 相關應用程式使用。

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 包含 Visual Studio 用來做為封裝和偵錯 SharePoint 專案、Office 應用程式及 SharePoint 相關應用程式之建置工作的類型。 這個應用程式開發介面支援 Office 和 SharePoint 基礎結構，但不適合直接在程式碼中使用。

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 包含用來自訂 SharePoint 專案的功能和封裝驗證行為的類型。

## <a name="see-also"></a>另請參閱
- [&#40;SharePoint 工具擴充性的參考&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [SharePoint 工具擴充功能的程式設計模型總覽](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
