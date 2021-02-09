---
title: 在 SharePoint 專案部署或撤銷時執行程式碼
titleSuffix: ''
description: 瞭解如何在 SharePoint 專案部署或撤銷時執行程式碼，讓您可以處理 Visual Studio 引發的事件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3362606a7e8c5f2278c2ebfb973321e5b8f3157e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850135"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>如何：在 SharePoint 專案部署或撤銷時執行程式碼
  如果您想要在 SharePoint 專案部署或撤銷時執行其他工作，您可以處理 Visual Studio 引發的事件。 如需詳細資訊，請參閱 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>若要在 SharePoint 專案部署或撤銷時執行程式碼

1. 建立專案專案延伸、專案延伸或新專案專案類型的定義。 如需詳細資訊，請參閱下列主題：

   - [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 在擴充功能中，存取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件。 如需詳細資訊，請參閱 [如何：取得 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。

3. 處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 專案服務的和事件。

4. 在事件處理常式中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> 參數來取得目前部署會話的相關資訊。 例如，您可以判斷哪個專案在目前的部署會話中，以及它是否正在進行部署或撤銷。

   下列程式碼範例示範如何處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 專案延伸中的和事件。 當 SharePoint 專案的部署開始和完成時，此延伸模組會將額外的訊息寫入至 [ **輸出** ] 視窗。

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [如何：在執行部署步驟時執行程式碼](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
