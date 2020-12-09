---
title: 匯入可重複使用工作流程的指導方針 |Microsoft Docs
description: 請參閱將 SharePoint Designer 中建立之可重複使用的工作流程匯入 Visual Studio 的指導方針。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: aab3d3b73fac086c4ff5aee8b5319a76e9aaea15
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915514"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>匯入可重複使用工作流程的指導方針
  若要匯入以 SharePoint Designer 所建立可重複使用的工作流程，請使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 [匯入可重複使用的 SharePoint 2010 工作流程] 專案範本。 此範本只會將 *宣告* 式 *工作流程* 匯入 ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]) ，並將它轉換成程式 *代碼工作* 流程，您可以使用或程式碼來增強此工作流程 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。

 不過，[匯入可重複使用的 SharePoint 2010 工作流程] 範本只能匯入陣列方案。 如果您要部署工作流程做為沙箱化方案，請使用 [匯入 SharePoint 2010 方案套件] 範本匯入工作流程。 但採用這種方式將無法將其轉換成程式碼工作流程，因而無法加以修改。

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>使用匯入可重複使用工作流程範本匯入可重複使用的工作流程
 如果您使用 [匯入可重複使用的 SharePoint 2010 工作流程] 範本匯入可重複使用的工作流程，您可以像對任何其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 方案一樣執行或變更方案，但您必須手動修正某些項目。

### <a name="import-task-forms"></a>匯入工作表單
 [匯入可重複使用的 SharePoint 2010 工作流程] 專案範本會匯入所有的初始表單和關聯表單，但只會匯入一份工作表單，這是因為程式碼工作流程結構描述僅允許一份工作表單。 原始工作流程解決方案中的任何其他工作表單都會放入 **方案總管** 的 [**其他匯入** 檔案] 資料夾中。

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>使用匯入 SharePoint 2010 方案套件範本匯入可重複使用的工作流程
 如果要使用 [匯入 SharePoint 2010 方案套件] 範本匯入可重複使用的工作流程，您必須考慮下列問題：

- 匯入工作流程之後，您可以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 選擇 **F5** 鍵立即在中部署和執行工作流程。 但是，如果您在匯入的方案中變更工作流程中的任何專案，您可能必須先手動修正專案中的元素，然後才能部署和執行工作流程。

- 因為工作流程是宣告式的，所以無法將程式碼新增至程式碼。 若要將工作流程轉換成程式碼工作流程，您必須 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用 [匯入可重複使用的 SharePoint 2010 工作流程] 範本將其匯入到中。

- 雖然您可以在設計檢視中編輯工作流程設計工具 (. xoml) 檔案，但建議您在來源視圖中進行編輯，因為工作流程設計工具會顯示錯誤錯誤。

- 在工作流程中的偵錯工具不適用於宣告式內容。 不會叫用在中設定的中斷點 [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] 。

## <a name="import-globally-reusable-workflow-solutions"></a>匯入可全域重複使用的工作流程解決方案
 您無法使用 [匯入可重複使用的 SharePoint 2010 工作流程] 範本匯入可全域重複使用的工作流程。 若要匯入可全域重複使用的工作流程，您必須將其轉換成無法全域重複使用的工作流程，或必須使用 [匯入 SharePoint 2010 方案套件] 範本。

 若要轉換工作流程，請開啟工作流程的快捷方式功能表，然後選擇 [ **另存為複製**) ，以在 SharePoint (Designer 中建立可全域重複使用的工作流程複本。 接著使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的 [匯入可重複使用的 SharePoint 2010 工作流程] 範本，匯入可重複使用的新工作流程。

 若要以原狀匯入可全域重複使用的工作流程，請使用 [匯入 SharePoint 2010 方案套件] 範本。 若您使用這個方法，工作流程並不會轉換成程式碼工作流程，而會保持為宣告式工作流程。

## <a name="see-also"></a>另請參閱
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
