---
title: 工作流程中的表單支援 |Microsoft Docs
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
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986254"
---
# <a name="form-support-in-workflows"></a>工作流程中的表單支援
  工作流程中可使用四種類型的表單：關聯、起始、工作和修改。 這些表單類型可以根據 ASPX 表單或 InfoPath 表單。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 提供給特定表單的支援層級取決於數個因素，如下表所述。 如需工作流程表單類型的詳細資訊，請參閱[工作流程表單總覽](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14))。

## <a name="xml-refactoring"></a>XML 重構
 當您將 ASPX 關聯或初始表單加入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流程專案專案時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會自動重構工作流程的*元素 .xml*檔案中的 XML，以保留參考關聯或初始表單同步的屬性。只要更新表單名稱或部署路徑，或刪除表單。 不過，當您在工作流程中使用其他表單類型時（例如工作或修改表單），不會重構*元素 .xml*檔案。

## <a name="form-support-in-new-visual-studio-workflows"></a>新 Visual Studio 工作流程中的表單支援
 下表列出在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中建立的工作流程中，在 ASPX 或 InfoPath 表單上的不同表單類型 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 支援。

|表單類型|在 Visual Studio 中使用 ASPX 表單建立的工作流程|使用 InfoPath 表單在 Visual Studio 中建立的工作流程|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|關聯|-您可以使用**工作流程關聯表單**專案範本，將 ASPX 關聯表單加入至工作流程。<br />-新增、重新命名或刪除表單時，或其部署路徑變更時，會重構工作流程的*Elements .xml*檔案。<br />-如需詳細資訊，請參閱[逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中沒有 InfoPath 關聯表單範本。<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 InfoPath Designer 之間沒有整合。<br />-未重構工作流程的*元素 .xml*檔案。|
|提出|-您可以使用**工作流程初始表單**專案範本，將 ASPX 初始表單加入至工作流程。<br />-新增、重新命名或刪除表單時，或其部署路徑變更時，會重構工作流程的*Elements .xml*檔案。<br />-如需詳細資訊，請參閱[逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中沒有 InfoPath 關聯表單範本。<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 InfoPath Designer 之間沒有整合。<br />-未重構工作流程的*元素 .xml*檔案。|
|工作|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中沒有可用的 ASPX 工作表單範本。 您必須建立應用程式頁面，並在其中加入程式碼。<br />-未重構工作流程的*元素 .xml*檔案。<br />-如需詳細資訊，請參閱[工作流程工作表單（SharePoint Foundation）](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中沒有 InfoPath 工作表單範本。<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 InfoPath Designer 之間沒有整合。<br />-未重構工作流程的*元素 .xml*檔案。|
|他人|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不提供 ASPX 修改表單範本。 若要加入修改表單，您必須建立應用程式頁面，並在其中加入程式碼。<br />-未重構工作流程的*元素 .xml*檔案。 您必須視需要手動編輯它。<br />-如需詳細資訊，請參閱[工作流程修改表單（SharePoint Foundation）](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中沒有 InfoPath 修改表單範本。<br />-[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 InfoPath Designer 之間沒有整合。<br />-未重構工作流程的*元素 .xml*檔案。|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>匯入的 SharePoint 可重複使用工作流程中的表單支援
 下表列出在 SharePoint 可重複使用的工作流程（匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]）中，不同表單類型的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 支援。

|表單類型|從 SharePoint Designer 匯入 ASPX 表單的可重複使用工作流程|從 SharePoint Designer 匯入 InfoPath 表單的可重複使用工作流程|
|---------------|-------------------------------------------------------------------------------| - |
|關聯|-表單會在工作流程的*Elements .xml*檔案中參考。<br />-重新命名或刪除表單時，或在其部署路徑變更時，會重構工作流程的*Elements .xml*檔案。|-表單已匯入，但未在工作流程的*元素*中參考。<br />-未重構工作流程的*元素 .xml*檔案。|
|提出|-表單是由工作流程之*Elements .xml*檔案中的工作流程所參考。<br />-重新命名或刪除表單時，或在其部署路徑變更時，會重構工作流程的*Elements .xml*檔案。|-表單已匯入，但未在工作流程的*元素*中參考。<br />-未重構工作流程的*元素 .xml*檔案。 **注意：** 您必須新增和變更規則和屬性，才能讓此案例生效。|
|工作|-表單會在工作流程的*Elements .xml*檔案中參考。<br />-未重構工作流程的*元素 .xml*檔案。|-表單已匯入，但未在工作流程的*元素*中參考。<br />-未重構工作流程的*元素 .xml*檔案。 **注意：** 您必須新增和變更規則和屬性，才能讓此案例生效。|
|他人|不適用。 無法在 SharePoint Designer 中建立 ASPX 修改表單。|不適用。 InfoPath 修改表單無法在 SharePoint Designer 中建立，除了內建的 SharePoint Server 工作流程（在匯出工作流程時，不會包含在 .wsp 檔案中）。|

## <a name="see-also"></a>請參閱
- [逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
