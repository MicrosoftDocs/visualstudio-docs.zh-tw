---
title: "如何： 執行程式碼時部署步驟 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ad603c9f303cd5bf2b3dc317efddd2694e10a867
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>如何：在執行部署步驟時執行程式碼
  如果您想要執行部署步驟 SharePoint 專案中的其他工作，您可以處理由 SharePoint 專案項目之前和之後 Visual Studio 會執行部署的每個步驟都會產生的事件。 如需詳細資訊，請參閱[擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>若要執行部署步驟時執行程式碼  
  
1.  建立專案項目擴充功能、 專案的副檔名或新的專案項目類型的定義。 如需詳細資訊，請參閱下列主題：  
  
    -   [如何：建立 SharePoint 專案項目延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  擴充功能，在處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>（在專案項目擴充功能或專案擴充功能） 的物件或<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>物件 （在新的專案項目類型定義）。  
  
3.  在事件處理常式，會使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs>和<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs>參數，以取得部署步驟的相關資訊。 例如，您可以判斷正在執行哪一個部署步驟和方案是否正在部署或撤銷。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>清單執行個體的專案項目擴充功能中的事件。 此延伸模組會將其他訊息寫入**輸出**視窗時，Visual Studio 部署及撤銷方案時，回收應用程式集區。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [如何：在 SharePoint 專案部署或撤銷時執行程式碼](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  