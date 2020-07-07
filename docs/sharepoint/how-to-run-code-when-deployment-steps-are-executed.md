---
title: 如何：在執行部署步驟時執行程式碼 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b2b0431ab4f985d801a78159fc2d324a29f8b638
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015533"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>如何：在執行部署步驟時執行程式碼
  如果您想要針對 SharePoint 專案中的部署步驟執行其他工作，您可以處理 SharePoint 專案專案在 Visual Studio 執行每個部署步驟之前和之後所引發的事件。 如需詳細資訊，請參閱[擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。

### <a name="to-run-code-when-deployment-steps-are-executed"></a>若要在執行部署步驟時執行程式碼

1. 建立專案專案延伸、專案延伸或新專案專案類型的定義。 如需詳細資訊，請參閱下列主題：

    - [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 在擴充功能中，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 物件的和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> （在專案專案延伸模組或專案延伸中）或 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 物件（在新專案專案類型的定義中）。

3. 在事件處理常式中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> 和 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> 參數來取得部署步驟的相關資訊。 例如，您可以判斷正在執行的部署步驟，以及是否正在部署或撤銷方案。

## <a name="example"></a>範例
 下列程式碼範例示範如何 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 針對清單實例專案專案，處理延伸模組中的和事件。 當 Visual Studio 在部署和撤銷解決方案時回收應用程式集區時，此延伸模組會將額外的訊息寫入至 [**輸出**] 視窗。

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列元件：

- VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件建立擴充功能（VSIX）封裝，以及您想要與延伸模組一起散發的任何其他檔案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [如何：在 SharePoint 專案部署或撤銷時執行程式碼](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
