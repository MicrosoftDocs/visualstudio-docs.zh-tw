---
title: 如何：處理部署衝突 |Microsoft Docs
description: 請參閱如何執行您自己的程式碼，以處理 SharePoint 專案專案部署衝突的範例。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c163aa10bdcb3ee28de6d6950dd15f85df876bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885608"
---
# <a name="how-to-handle-deployment-conflicts"></a>如何：處理部署衝突
  您可以提供自己的程式碼來處理 SharePoint 專案專案的部署衝突。 例如，您可以判斷目前專案專案中的任何檔案是否已存在於部署位置中，然後在部署目前的專案專案之前，先刪除已部署的檔案。 如需部署衝突的詳細資訊，請參閱 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。

### <a name="to-handle-a-deployment-conflict"></a>處理部署衝突

1. 建立專案專案延伸、專案延伸或新專案專案類型的定義。 如需詳細資訊，請參閱下列主題：

    - [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 在擴充功能中，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 專案專案延伸或專案延伸中的物件 (的事件) 或) 的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 新專案專案類型定義中 (物件。

3. 在事件處理常式中，根據適用于您案例的準則，判斷要部署的專案專案與 SharePoint 網站上部署的方案之間是否發生衝突。 您可以使用 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> 事件引數參數的屬性來分析正在部署的專案專案，而且可以藉由呼叫您針對此目的定義的 SharePoint 命令，在部署位置分析檔案。

     對於許多類型的衝突，您可能會先決定要執行哪個部署步驟。 您可以使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> 事件引數參數的屬性來進行這項作業。 雖然在內建的部署步驟中偵測到衝突通常是合理的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> ，但您可以在任何部署步驟期間檢查是否有衝突。

4. 如果有衝突存在，請使用 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> 事件引數的屬性方法來建立新的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 物件。 此物件代表部署衝突。 在呼叫 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 方法時，也要指定呼叫以解決衝突的方法。

## <a name="example"></a>範例
 下列程式碼範例示範針對清單定義專案專案，在專案專案延伸中處理部署衝突的基本處理常式。 若要處理不同類型專案專案的部署衝突，請將不同的字串傳遞給 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 。 如需詳細資訊，請參閱 [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)。

 為了簡單起見， <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 此範例中的事件處理常式會假設部署衝突存在 (也就是，它一律會將新的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 物件加入) ，而此 `Resolve` 方法只會傳回 **true** ，表示衝突已解決。 在實際案例中， <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件處理常式會先判斷目前專案專案中的檔案和部署位置的檔案之間是否有衝突，然後 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 只有在衝突存在時才新增物件。 例如，您可以使用 `e.ProjectItem.Files` 事件處理常式中的屬性來分析專案專案中的檔案，而且您可能會呼叫 SharePoint 命令來分析部署位置的檔案。 同樣地，在實際的案例中，此 `Resolve` 方法可能會呼叫 sharepoint 命令以解決 sharepoint 網站上的衝突。 如需建立 SharePoint 命令的詳細資訊，請參閱 [如何：建立 sharepoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)。

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)
- [如何：在執行部署步驟時執行程式碼](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [如何：建立 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)
