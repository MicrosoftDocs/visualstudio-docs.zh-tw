---
title: 如何：在執行部署步驟時執行程式碼 |Microsoft Docs
description: 執行程式碼，以處理 SharePoint 專案專案在 Visual Studio 執行部署步驟之前和之後所引發的事件。
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
ms.openlocfilehash: 74db1b73dded52ba15ea860873c49c0264f7fea7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214404"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>如何：在執行部署步驟時執行程式碼
  如果您想要針對 SharePoint 專案中的部署步驟執行其他工作，您可以在 Visual Studio 執行每個部署步驟之前和之後，處理 SharePoint 專案專案所引發的事件。 如需詳細資訊，請參閱 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。

### <a name="to-run-code-when-deployment-steps-are-executed"></a>若要在執行部署步驟時執行程式碼

1. 建立專案專案延伸、專案延伸或新專案專案類型的定義。 如需詳細資訊，請參閱下列主題：

    - [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 在擴充功能中，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 專案專案延伸或專案延伸中的物件 (和事件) 或 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>) 新專案專案類型的定義中 (物件。

3. 在事件處理常式中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> 和 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> 參數來取得部署步驟的相關資訊。 例如，您可以判斷正在執行的部署步驟，以及解決方案是否正在進行部署或撤銷。

## <a name="example"></a>範例
 下列程式碼範例示範如何處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 清單實例專案專案擴充功能中的和事件。 當 Visual Studio 在部署和撤銷解決方案時回收應用程式集區時，此擴充功能會將額外的訊息寫入至 **輸出** 視窗。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb" id="Snippet4":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs" id="Snippet4":::

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [如何：在 SharePoint 專案部署或撤銷時執行程式碼](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
