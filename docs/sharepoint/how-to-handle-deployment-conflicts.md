---
title: HOW TO：處理部署衝突 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d55c260618eb7edcf68e91b521f2ace203ddbf01
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898878"
---
# <a name="how-to-handle-deployment-conflicts"></a>HOW TO：處理部署衝突
  您可以提供您自己的程式碼來處理部署衝突的 SharePoint 專案項目。 例如，您可能會判斷目前的專案項目中的任何檔案是否存在於部署位置，和之前部署目前的專案項目，然後刪除已部署的檔案。 如需有關部署衝突的詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-handle-a-deployment-conflict"></a>若要處理部署衝突  
  
1.  建立專案項目延伸模組、 專案擴充功能或新的專案項目類型定義。 如需詳細資訊，請參閱下列主題：  
  
    -   [如何：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在 擴充功能，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件的<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>（在專案項目擴充功能或專案擴充功能） 的物件或<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>物件 （在新的專案項目類型定義）。  
  
3.  在 事件處理常式中，判斷是否有正在部署的專案項目與已部署的解決方案上 SharePoint 網站，根據適用於您案例的條件之間有衝突。 您可以使用<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>的事件引數參數，以分析部署的是，專案項目屬性，您可以藉由呼叫您定義針對此用途的 SharePoint 命令分析在部署位置的檔案。  
  
     對於許多種衝突的詳細資訊，您可能會首先要決定執行哪一個部署步驟。 您可以使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A>事件引數參數的屬性。 雖然通常是合理的期間內建偵測衝突<xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>部署步驟中，您可以在任何部署步驟期間檢查衝突。  
  
4.  如果發生衝突，使用<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>方法<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A>屬性來建立新的事件引數<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>物件。 此物件表示部署衝突。 在您呼叫<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>方法，也指定呼叫來解決衝突的方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何處理部署衝突清單定義專案項目的專案項目擴充功能中的 basic 程序。 若要處理不同類型的專案項目的部署衝突，傳遞到不同的字串<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。  
  
 為了簡單起見，<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件處理常式，在此範例假設部署衝突存在 (亦即，它一律會將新<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>物件)，而`Resolve`方法只會傳回 **，則為 true**表示衝突解決的時間。 在真實的案例中，您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件處理常式會先判斷目前的專案項目中的檔案和部署位置的檔案之間有衝突，然後新增<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>物件衝突是否存在。 例如，您可以使用`e.ProjectItem.Files`分析中的檔案的專案項目，以及您的事件處理常式的屬性可能會呼叫 SharePoint 命令，以分析在部署位置的檔案。 同樣地，在真實案例`Resolve`方法可能會呼叫 SharePoint 命令，以解決在 SharePoint 網站上的衝突。 如需建立 SharePoint 命令的詳細資訊，請參閱[How to:建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>部署擴充功能  
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [如何：執行部署步驟時執行程式碼](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [如何：建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)  
