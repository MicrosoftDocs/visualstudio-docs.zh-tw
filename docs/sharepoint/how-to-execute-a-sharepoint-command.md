---
title: 如何：執行 SharePoint 命令 |Microsoft Docs
description: 閱讀如何建立自訂 SharePoint 命令，以從 SharePoint 工具延伸模組呼叫伺服器物件模型 API。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b5a9ea96820aafe32ca119d7e6d08057b91206fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943818"
---
# <a name="how-to-execute-a-sharepoint-command"></a>How to：執行 SharePoint 命令
  如果您想要在 SharePoint 工具擴充功能中使用伺服器物件模型，您必須建立自訂 *SharePoint 命令* 以呼叫 API。 在您定義命令並使用 SharePoint 工具延伸模組部署之後，您的擴充功能就可以執行命令來呼叫 SharePoint 伺服器物件模型。 若要執行命令，請使用物件的其中一個 ExecuteCommand 方法 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 。

 如需有關 SharePoint 命令用途的詳細資訊，請參閱 [呼叫 sharepoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

### <a name="to-execute-a-sharepoint-command"></a>若要執行 SharePoint 命令

1. 在您的 SharePoint 工具擴充功能中，取得 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 物件。 您取得物件的方式 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 取決於您所建立的延伸模組類型：

    - 在 SharePoint 專案系統的延伸中，請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> 屬性。

         如需有關專案系統擴充功能的詳細資訊，請參閱 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

    - 在 **伺服器總管** 的 [ **SharePoint 連接**] 節點的延伸中，使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> 屬性。 若要取得 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> 物件，請使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> 屬性。

         如需 **伺服器總管** 擴充功能的詳細資訊，請參閱 [伺服器總管中的擴充 SharePoint 連接節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。

    - 在不屬於 SharePoint 工具延伸模組的程式碼中（例如專案範本 wizard），請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 屬性。

         如需有關如何取出專案服務的詳細資訊，請參閱 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

2. 呼叫物件的其中一個 ExecuteCommand 方法 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 。 將您想要執行的命令名稱傳遞至 ExecuteCommand 方法的第一個引數。 如果您的命令有自訂參數，請將該參數傳遞給 ExecuteCommand 方法的第二個引數。

     每個支援的命令簽章都有不同的 ExecuteCommand 多載。 下表列出支援的簽章，以及要用於每個簽章的多載。

    |命令簽章|要使用的 ExecuteCommand 多載|
    |-----------------------|------------------------------------|
    |此命令只有預設 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數和沒有傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |此命令只有預設 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數和傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |此命令有兩個參數 (預設 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數和自訂參數) ，而且沒有傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |此命令有兩個參數和一個傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>範例
 下列程式碼範例示範如何使用多載 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 來呼叫 how `Contoso.Commands.UpgradeSolution` [to： Create a SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)所述的命令。

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute`此範例中顯示的方法是 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 在自訂部署步驟中執行介面的方法。 若要在較大範例的內容中查看這個程式碼，請參閱 [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

 請注意下列有關呼叫方法的詳細資料 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> ：

- 第一個參數會識別您想要呼叫的命令。 這個字串符合您傳遞至 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 命令定義上的值。

- 第二個參數是您想要傳遞給命令之自訂第二個參數的值。 在此情況下，它是要升級至 SharePoint 網站之 *.wsp* 檔案的完整路徑。

- 程式碼不會將隱含 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數傳遞至命令。 當您從 SharePoint 專案系統的延伸模組或 **伺服器總管** 中的 [ **sharepoint 連接**] 節點的延伸模組呼叫命令時，會自動將此參數傳遞至命令。 在其他類型的方案中，例如在執行介面的專案範本嚮導中 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> ，此參數為 **null**。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要 VisualStudio 元件的參考。

## <a name="see-also"></a>另請參閱
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [如何：建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
