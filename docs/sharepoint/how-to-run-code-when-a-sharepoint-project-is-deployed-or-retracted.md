---
title: HOW TO：執行程式碼時在 SharePoint 專案是部署或撤銷 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb5ba251df3271e704ea4b455c5cc47003ab8e2e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933618"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>HOW TO：SharePoint 專案部署或撤銷時執行程式碼
  如果您想要部署或撤回 SharePoint 專案時執行其他工作，您可以處理由 Visual Studio 所引發的事件。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>若要執行的程式碼時的 SharePoint 專案部署或撤銷  
  
1. 建立專案項目延伸模組、 專案擴充功能或新的專案項目類型定義。 如需詳細資訊，請參閱下列主題：  
  
   -   [如何：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
   -   [如何：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
   -   [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2. 在 擴充功能，存取<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>物件。 如需詳細資訊，請參閱[＜How to：擷取 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。  
  
3. 處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>專案服務的事件。  
  
4. 在事件處理常式，使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs>參數，以取得目前的部署工作階段的相關資訊。 例如，您可以判斷哪一個專案是目前的部署工作階段中，而且是否正在部署或撤銷。  
  
   下列程式碼範例示範如何處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>專案擴充功能中的事件。 此延伸模組會將其他訊息寫入**輸出**視窗時部署的開始和完成的 SharePoint 專案。  
  
   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [如何：執行部署步驟時執行程式碼](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
