---
title: 匯入可重複使用的工作流程的指導方針 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7e32ba1641b084f1240e2a3f872a07e410b6c507
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641516"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>匯入可重複使用的工作流程的指導方針
  若要匯入以 SharePoint Designer 所建立可重複使用的工作流程，請使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 [匯入可重複使用的 SharePoint 2010 工作流程] 專案範本。 此範本會匯入*宣告**工作流程*([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-只)，並將它轉換*程式碼工作流程*，這是您可以使用增強的工作流程[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]或[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]程式碼。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [逐步解說：SharePoint Designer 可重複使用工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。

 不過，[匯入可重複使用的 SharePoint 2010 工作流程] 範本只能匯入陣列方案。 如果您要部署工作流程做為沙箱化方案，請使用 [匯入 SharePoint 2010 方案套件] 範本匯入工作流程。 但採用這種方式將無法將其轉換成程式碼工作流程，因而無法加以修改。

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>使用匯入可重複使用工作流程範本匯入可重複使用的工作流程
 如果您使用 [匯入可重複使用的 SharePoint 2010 工作流程] 範本匯入可重複使用的工作流程，您可以像對任何其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 方案一樣執行或變更方案，但您必須手動修正某些項目。

### <a name="import-task-forms"></a>匯入工作表單
 [匯入可重複使用的 SharePoint 2010 工作流程] 專案範本會匯入所有的初始表單和關聯表單，但只會匯入一份工作表單，這是因為程式碼工作流程結構描述僅允許一份工作表單。 從原始的工作流程方案的任何額外的工作表單會放入**其他匯入檔案**中的資料夾**方案總管 中**。

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>使用匯入 SharePoint 2010 方案套件範本匯入可重複使用的工作流程
 如果要使用 [匯入 SharePoint 2010 方案套件] 範本匯入可重複使用的工作流程，您必須考慮下列問題：

-   匯入工作流程之後, 可以立即部署並執行它[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]藉由選擇**F5**索引鍵。 不過，如果您變更任何項目匯入的方案中的工作流程中，您可能要手動修正項目在專案中，您可以部署及執行工作流程之前。

-   因為工作流程是宣告式，則程式碼不能加入至它。 若要將工作流程轉換成程式碼工作流程中，您必須匯入到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入的可重複使用 SharePoint 2010 工作流程範本。

-   雖然您可以編輯 設計 檢視中的工作流程設計工具 (.xoml) 檔案，建議，您在編輯原始碼 檢視中，因為工作流程設計工具會顯示 false 錯誤。

-   偵錯工作流程中無法用於宣告式的內容。 在中設定中斷點[!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)]不會叫用。

## <a name="import-globally-reusable-workflow-solutions"></a>匯入全域重複使用的工作流程方案
 您無法使用 [匯入可重複使用的 SharePoint 2010 工作流程] 範本匯入可全域重複使用的工作流程。 若要匯入可全域重複使用的工作流程，您必須將其轉換成無法全域重複使用的工作流程，或必須使用 [匯入 SharePoint 2010 方案套件] 範本。

 若要轉換的工作流程，請在 SharePoint Designer 中建立一份全域重複使用的工作流程 (開啟工作流程的捷徑功能表，然後選擇**存複本**)。 接著使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的 [匯入可重複使用的 SharePoint 2010 工作流程] 範本，匯入可重複使用的新工作流程。

 若要以原狀匯入可全域重複使用的工作流程，請使用 [匯入 SharePoint 2010 方案套件] 範本。 若您使用這個方法，工作流程並不會轉換成程式碼工作流程，而會保持為宣告式工作流程。

## <a name="see-also"></a>另請參閱
- [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [逐步解說：SharePoint Designer 可重複使用工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
