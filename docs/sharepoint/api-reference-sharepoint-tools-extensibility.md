---
title: API 參考 （SharePoint 工具擴充性） |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37639068b74b5d99864871355a8b9ef36906f6cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62987991"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>API 參考 （SharePoint 工具擴充性）
  本章節包含擴充 Visual Studio 中的 SharePoint 工具的 API 參考文件。

## <a name="in-this-section"></a>本節內容
 <xref:Microsoft.VisualStudio.SharePoint>

 包含您用來擴充 SharePoint 專案系統的型別。 例如，您可以擴充內建的 SharePoint 專案和專案項目，或您可以建立您自己的專案項目。

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 包含可用來建立自訂的型別*SharePoint 命令*。 SharePoint 命令是從 SharePoint 工具擴充功能呼叫 SharePoint 伺服器物件模型的方法。

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 包含您用來擴充 SharePoint 專案的部署程序的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 包含您用來擴充 SharePoint 節點中的型別**伺服器總管**或定義自己的節點型別。

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 包含可用來取得內建的相關資訊的型別**伺服器總管**節點代表 SharePoint 網站，例如代表清單、 欄位或內容類型的節點上的個別元件。

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 包含用來存取 SharePoint 專案中功能定義的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 包含您用來存取 SharePoint 專案中的封裝定義的型別。

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 包含用來驗證部署至遠端 SharePoint 網站的 SharePoint 相關應用程式及進行通訊的類型。

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 包含用來建立 SharePoint 遠端命令的類型，這些類型會搭配部署至遠端 SharePoint 網站的 SharePoint 相關應用程式使用。

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 包含 Visual Studio 用來做為封裝和偵錯 SharePoint 專案、Office 應用程式及 SharePoint 相關應用程式之建置工作的類型。 此 API 支援 Office 和 SharePoint 基礎結構，但不適合直接從您的程式碼使用。

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 包含用來自訂 SharePoint 專案的功能和封裝驗證行為的類型。

## <a name="see-also"></a>另請參閱
- [參考&#40;SharePoint 工具擴充性&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [概觀的程式設計模型的 SharePoint 工具擴充功能](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
