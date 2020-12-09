---
title: 工作流程中的表單支援 |Microsoft Docs
description: 閱讀 SharePoint 工作流程中表單支援的相關資訊。 您可以在工作流程中使用四種類型的表單：關聯、初始、工作和修改。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52939fe00dcbca1cfd633c81d4b0a00ea6b517b9
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915501"
---
# <a name="form-support-in-workflows"></a>工作流程中的表單支援
  您可以在工作流程中使用四種類型的表單：關聯、初始、工作和修改。 這些表單類型可以是以 ASPX 表單或 InfoPath 表單為基礎。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]針對特定表單提供的支援層級取決於數個因素，如下表所述。 如需工作流程表單類型的詳細資訊，請參閱 [工作流程](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14))表單總覽。

## <a name="xml-refactoring"></a>XML 重構
 當您將 ASPX 關聯或初始表單加入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流程專案專案時， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會自動重構工作流程 *Elements.xml* 檔中的 XML，以在更新表單名稱或部署路徑或刪除表單時，讓參考關聯或起始表單的屬性保持同步。 但是，當您在工作流程中使用其他表單類型時（例如工作或修改表單），不會重構 *Elements.xml* 檔案。

## <a name="form-support-in-new-visual-studio-workflows"></a>新 Visual Studio 工作流程中的表單支援
 下表列出在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立的工作流程中，對 ASPX 或 InfoPath 表單上不同表單類型的支援 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

|表單類型|以 ASPX 表單 Visual Studio 中建立的工作流程|使用 InfoPath 表單在 Visual Studio 中建立的工作流程|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|關聯|-您可以使用 **工作流程關聯表單** 專案範本，將 ASPX 關聯表單加入至工作流程。<br />-新增、重新命名或刪除表單時，或當其部署路徑變更時，會重構工作流程的 *Elements.xml* 檔案。<br />-如需詳細資訊，請參閱 [逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-中沒有 InfoPath 關聯表單範本 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-與 InfoPath 設計工具之間沒有整合 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-不會重構工作流程的 *Elements.xml* 檔案。|
|啟動|-您可以使用 **工作流程初始表單** 專案範本，將 ASPX 初始表單加入至工作流程。<br />-新增、重新命名或刪除表單時，或當其部署路徑變更時，會重構工作流程的 *Elements.xml* 檔案。<br />-如需詳細資訊，請參閱 [逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-中沒有 InfoPath 關聯表單範本 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-與 InfoPath 設計工具之間沒有整合 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-不會重構工作流程的 *Elements.xml* 檔案。|
|Task|-沒有任何 ASPX 工作表單範本可在中使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 您必須建立應用程式頁面，並在其中加入程式碼。<br />-不會重構工作流程的 *Elements.xml* 檔案。<br />-如需詳細資訊，請參閱 [ (SharePoint Foundation 的工作流程工作表單) ](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-中沒有 InfoPath 工作表單範本 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-與 InfoPath 設計工具之間沒有整合 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-不會重構工作流程的 *Elements.xml* 檔案。|
|修改|-在中不提供 ASPX 修改表單範本 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 若要加入修改表單，您必須建立應用程式頁面，並在其中加入程式碼。<br />-不會重構工作流程的 *Elements.xml* 檔案。 您必須視需要手動進行編輯。<br />-如需詳細資訊，請參閱 [ (SharePoint Foundation 的工作流程修改表單) ](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-中沒有 InfoPath 修改表單範本 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-與 InfoPath 設計工具之間沒有整合 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。<br />-不會重構工作流程的 *Elements.xml* 檔案。|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>匯入的 SharePoint 可重複使用工作流程中的表單支援
 下表列出 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在 SharePoint 可重複使用的工作流程中，針對匯入的 ASPX 或 InfoPath 表單上不同表單類型的支援 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

|表單類型|從 SharePoint Designer 匯入 ASPX 表單的可重複使用工作流程|從 SharePoint Designer 匯入 InfoPath 表單的可重複使用工作流程|
|---------------|-------------------------------------------------------------------------------| - |
|關聯|-表單會在工作流程的 *Elements.xml* 檔案中參考。<br />-重新命名或刪除表單或其部署路徑變更時，會重構工作流程的 *Elements.xml* 檔案。|-匯入表單，但不會在工作流程的 *Elements.xml* 中參考。<br />-不會重構工作流程的 *Elements.xml* 檔案。|
|啟動|-工作流程的 *Elements.xml* 檔案中的工作流程會參考表單。<br />-重新命名或刪除表單或其部署路徑變更時，會重構工作流程的 *Elements.xml* 檔案。|-匯入表單，但不會在工作流程的 *Elements.xml* 中參考。<br />-不會重構工作流程的 *Elements.xml* 檔案。 **注意：**  必須新增和變更規則和屬性，此案例才能運作。|
|Task|-表單會在工作流程的 *Elements.xml* 檔案中參考。<br />-不會重構工作流程的 *Elements.xml* 檔案。|-匯入表單，但不會在工作流程的 *Elements.xml* 中參考。<br />-不會重構工作流程的 *Elements.xml* 檔案。 **注意：**  必須新增和變更規則和屬性，此案例才能運作。|
|修改|不適用。 無法在 SharePoint Designer 中建立 ASPX 修改表單。|不適用。 InfoPath 修改表單無法在 SharePoint Designer 中建立，但內建的 SharePoint Server 工作流程除外，在匯出工作流程時，不會包含在 .wsp 檔案中。|

## <a name="see-also"></a>另請參閱
- [逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
