---
title: 擴充 SharePoint 封裝和部署 |Microsoft Docs
description: 擴充 SharePoint 封裝和部署。 建立部署步驟和設定。 處理部署衝突。 自訂驗證規則。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: cd4967e38738018f9b30365575a2dcb9e8970963
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948748"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>擴充 SharePoint 封裝和部署
  您可以擴充 SharePoint 專案的封裝和部署程序。

## <a name="create-deployment-steps"></a>建立部署步驟
 當您部署 SharePoint 專案時，[!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] 會執行一系列部署步驟。 Visual Studio 包含許多工作 (例如撤銷和加入解決方案) 的內建部署步驟。 不過，您也可以建立自己的部署步驟。

 如需示範如何建立部署步驟的逐步解說，請參閱 [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

## <a name="create-deployment-configurations"></a>建立部署設定
 部署組態是一組部署步驟，系統會針對指定的專案執行，但可能會影響所有 SharePoint 專案項目。 每個部署組態包括一組部署專案時所執行的步驟，和專案遭到撤銷時所執行的另一組步驟。 [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] 包含兩個內建的部署設定，但您也可以建立自己的部署設定。 當您建立部署組態時，您可以包含內建的部署步驟與您建立的部署步驟。

 如需示範如何建立部署設定的逐步解說，請參閱 [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>在 SharePoint 方案部署或撤銷時執行程式碼
 您可以處理事件，在部署或撤銷 SharePoint 方案時執行其他工作。 Visual Studio 會引發事件，您可以在下列情況下處理：

- 針對 SharePoint 專案項目，在每次部署前後執行步驟。 如需詳細資訊，請參閱 [如何：在執行部署步驟時](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)執行程式碼。

- 在 SharePoint 專案部署或撤銷前後。 如需詳細資訊，請參閱 [如何：在 SharePoint 專案部署或撤銷時執行程式碼](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)。

## <a name="handle-deployment-conflicts"></a>處理部署衝突
 某些類型的 SharePoint 專案項目 (包括模組、Web 組件、清單執行個體和內容類型) 提供內建的部署衝突解決方式。 當您部署包含其中一個專案項目的方案時，Visual Studio 會先檢查 SharePoint 網站上的檔案，與您正在部署的項目中檔案是否具有相同的名稱、URL 或 ID。 如果發生衝突，Visual Studio 可以自動解決衝突，或提示您決定是否要讓 Visual Studio 解決衝突或取消部署。 如需詳細資訊，請參閱 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)。

 您可以提供您自己的程式碼來檢查並解決部署衝突，以擴充此功能。 如需詳細資訊，請參閱 [如何：處理部署衝突](../sharepoint/how-to-handle-deployment-conflicts.md)。

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>在部署專案之前或之後執行命令列作業
 如果您想要在部署 SharePoint 方案後執行命令列作業，您可以設定 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> 屬性。 Visual Studio 會在部署專案的之前或之後執行這些命令。

 在某些情況下，您可能會看到部署衝突。 有幾種不同的方式可解決衝突。 如需詳細資訊，請參閱 [疑難排解 SharePoint 封裝和部署](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)。

## <a name="customize-validation-rules"></a>自訂驗證規則
 部署方案套件 (.wsp) 之前，您可以建立自訂的功能和封裝驗證規則來驗證功能或封裝是否有效。 比方說，您可以向開發人員報告資訊、警告或錯誤以協助修正驗證問題。 如需詳細資訊，請參閱 [如何：建立 SharePoint 方案的自訂功能和封裝驗證規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。

## <a name="see-also"></a>另請參閱
- [如何：在執行部署步驟時執行程式碼](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [如何：建立 SharePoint 方案的自訂功能和套件驗證規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
