---
title: 如何： 執行程式碼部署步驟時執行 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: cebd88cc49afa1092dfcd1d67ffdbf0fa3567ad0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118723"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>如何： 執行部署步驟時執行程式碼
  如果您想要執行的 SharePoint 專案中的部署步驟的其他工作，您可以處理的 SharePoint 專案項目之前和之後 Visual Studio 會執行每個部署步驟引發的事件。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>若要執行部署步驟時執行程式碼  
  
1.  建立專案項目延伸模組、 專案擴充功能或新的專案項目類型定義。 如需詳細資訊，請參閱下列主題：  
  
    -   [如何： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何： 定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在擴充功能，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>並<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>的事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>（在專案項目擴充功能或專案擴充功能） 的物件或<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>物件 （在新的專案項目類型定義）。  
  
3.  在事件處理常式，使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs>和<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs>參數，以取得部署步驟的相關資訊。 比方說，您可以在其中決定執行哪一個部署步驟，以及解決方案是否正在部署或撤銷。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>清單執行個體的專案項目的延伸模組中的事件。 此延伸模組會將其他訊息寫入**輸出**時 Visual Studio 部署和正在撤銷方案時回收應用程式集區 視窗。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [如何： 部署或撤回 SharePoint 專案時執行程式碼](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  
