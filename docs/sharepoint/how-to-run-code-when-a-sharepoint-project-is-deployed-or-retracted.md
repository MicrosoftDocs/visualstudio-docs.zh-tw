---
title: "如何： 執行程式碼時在 SharePoint 專案是部署或撤銷 |Microsoft 文件"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0650bfdb7961728fed34147c05f6333d8255e373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>如何：在 SharePoint 專案部署或撤銷時執行程式碼
  如果您想要部署或撤回 SharePoint 專案時執行額外的工作，您可以處理由 Visual Studio 所引發的事件。 如需詳細資訊，請參閱[擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>若要執行的程式碼時的 SharePoint 專案部署或撤銷  
  
1.  建立專案項目擴充功能、 專案的副檔名或新的專案項目類型的定義。 如需詳細資訊，請參閱下列主題：  
  
    -   [如何：建立 SharePoint 專案項目延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在 [延伸] 存取<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件。 如需詳細資訊，請參閱[How to： 擷取 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。  
  
3.  處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>專案服務的事件。  
  
4.  在事件處理常式，會使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs>參數，以取得目前的部署工作階段的相關資訊。 例如，您可以判斷哪一個專案是目前的部署工作階段中，而且是否會部署或撤銷。  
  
 下列程式碼範例示範如何處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>專案擴充功能中的事件。 此延伸模組會將其他訊息寫入**輸出**部署開始和完成 SharePoint 專案時，視窗。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [如何：在執行部署步驟時執行程式碼](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  