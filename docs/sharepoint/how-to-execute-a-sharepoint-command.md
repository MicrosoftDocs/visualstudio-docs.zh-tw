---
title: "如何： 執行 SharePoint 命令 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], executing
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1cfe20d0cac50603265644fb48102ef22537631
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-execute-a-sharepoint-command"></a>如何：執行 SharePoint 命令
  如果您想要使用伺服器物件模型中的 SharePoint 工具擴充功能，您必須建立自訂*SharePoint 命令*來呼叫 API。 定義命令，並將它部署在與您的 SharePoint 工具擴充功能之後，您的延伸模組可以執行命令來呼叫 SharePoint 伺服器物件模型。 若要執行此命令，使用其中一個的 ExecuteCommand 方法<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>物件。  
  
 如需有關 SharePoint 命令的用途的詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### <a name="to-execute-a-sharepoint-command"></a>若要執行 SharePoint 命令  
  
1.  在您的 SharePoint 工具擴充功能，取得<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>物件。 您所取得的方式<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>物件取決於您所建立的延伸的型別：  
  
    -   在 SharePoint 專案系統的延伸模組，使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>屬性。  
  
         如需專案系統擴充功能的詳細資訊，請參閱[擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
    -   中的延伸模組**SharePoint 連接**節點**伺服器總管**，使用<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>屬性。 若要取得<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>物件，請使用<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>屬性。  
  
         如需有關**伺服器總管**擴充功能，請參閱[擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
    -   在不是專案範本 」 精靈中，例如與 SharePoint 工具的擴充功能的一部分的程式碼使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>屬性。  
  
         如需擷取專案服務的詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
2.  呼叫其中一個 ExecuteCommand 方法<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>物件。 傳遞要 ExecuteCommand 方法的第一個引數所執行的命令名稱。 如果您的命令有自訂的參數，請將該參數傳遞至 ExecuteCommand 方法的第二個引數。  
  
     沒有 ExecuteCommand 多載的每個支援的命令簽章不同。 下表列出支援的簽章和其多載，要用於每個簽章。  
  
    |命令的簽章|若要使用的 ExecuteCommand 多載|  
    |-----------------------|------------------------------------|  
    |命令具有預設值<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>參數且沒有傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |命令具有預設值<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>參數和傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |命令具有兩個參數 (預設值<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>參數，並自訂參數) 且沒有傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |命令具有兩個參數和傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>多載來呼叫`Contoso.Commands.UpgradeSolution`命令中所述[How to： 建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute`範例所示的方法是實作<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A>方法<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>介面中的自訂部署步驟。 若要查看此程式碼之較大範例的內容中，請參閱[逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
 請注意下列詳細資料相關的呼叫<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>方法：  
  
-   第一個參數會識別您想要呼叫的命令。 這個字串比對的值傳遞給<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>命令定義。  
  
-   第二個參數是您想要傳遞給自訂命令的第二個參數的值。 在此情況下，它是正在升級至 SharePoint 網站的.wsp 檔案的完整路徑。  
  
-   程式碼沒有通過隱含<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>命令的參數。 這個參數會傳遞到命令自動當您呼叫命令中的 SharePoint 專案系統擴充功能或延伸**SharePoint 連接**節點**伺服器總管**. 在其他類型的解決方案，例如實作專案範本精靈<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面，這個參數是**null**。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要 Microsoft.VisualStudio.SharePoint 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [如何： 建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [逐步解說：擴充伺服器總管以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  