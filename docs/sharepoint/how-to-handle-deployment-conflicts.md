---
title: "如何： 處理部署衝突 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: c3bbd5bc7d69fbc48d2c754151a3ec6b5fcb612c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-handle-deployment-conflicts"></a>如何：處理部署衝突
  您可以提供您自己的程式碼來處理部署衝突 SharePoint 專案項目。 例如，您可能會判斷目前的專案項目中的任何檔案是否存在於部署位置，並部署目前的專案項目之前，然後刪除已部署的檔案。 如需有關部署衝突的詳細資訊，請參閱[擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-handle-a-deployment-conflict"></a>處理部署衝突  
  
1.  建立專案項目擴充功能、 專案的副檔名或新的專案項目類型的定義。 如需詳細資訊，請參閱下列主題：  
  
    -   [如何：建立 SharePoint 專案項目延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  擴充功能，在處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>（在專案項目擴充功能或專案擴充功能） 的物件或<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>物件 （在新的專案項目類型定義）。  
  
3.  中的事件處理常式，判斷是否有正在部署的專案項目與已部署的方案在 SharePoint 網站中，根據適用於您案例的準則之間的衝突。 您可以使用<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>來分析專案項目正在部署，事件引數參數的屬性，您可以藉由呼叫您針對此用途所定義的 SharePoint 命令分析在部署位置的檔案。  
  
     對於許多類型的衝突，您可能會第一次想要判斷哪一個部署步驟執行。 您可以使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A>事件引數參數的屬性。 雖然通常是合理的衝突偵測期間內建<xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>部署步驟中，您可以在任何部署步驟期間檢查衝突。  
  
4.  如果發生衝突，使用<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>方法<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A>屬性來建立新的事件引數的<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>物件。 這個物件代表部署衝突。 在您呼叫<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>方法，也指定呼叫來解決衝突的方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範處理部署衝突清單定義專案項目的專案項目擴充功能中的基本程序。 若要處理部署衝突，不同的專案項目類型，傳遞至不同的字串<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 如需詳細資訊，請參閱[擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。  
  
 為了簡單起見，<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件處理常式，在此範例假設部署衝突 (也就是它永遠會加入新<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>物件)，而`Resolve`方法只會傳回**true**表示衝突解決的時間。 在實際案例中，您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件處理常式會先判斷目前的專案項目中的檔案和部署位置的檔案之間有衝突，然後再加入<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>物件衝突是否存在。 例如，您可能會使用`e.ProjectItem.Files`分析中的檔案的專案項目，以及您的事件處理常式的屬性可能會呼叫 SharePoint 命令來分析在部署位置的檔案。 同樣地，在真實案例`Resolve`方法可能會呼叫來解決衝突，在 SharePoint 網站上的 SharePoint 命令。 如需有關建立 SharePoint 命令的詳細資訊，請參閱[How to： 建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [如何： 執行程式碼時部署步驟](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [如何：建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  