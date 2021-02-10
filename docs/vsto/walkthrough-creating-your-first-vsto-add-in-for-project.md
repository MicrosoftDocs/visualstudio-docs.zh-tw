---
title: 逐步解說：建立 Project 的第一個 VSTO 增益集
description: 建立 Microsoft Project 的應用層級增益集。 這項功能適用于應用程式本身，不論開啟了哪些專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f35649db5f61cb545bb3550980b3d6b9a8742cd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966496"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>逐步解說：建立 Project 的第一個 VSTO 增益集
  本逐步解說將說明如何建立 Microsoft Office 專案的 VSTO 增益集。 不論開啟哪一個專案，您在這類方案中建立的功能都可供應用程式本身使用。 如需詳細資訊，請參閱 [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 本逐步解說將說明下列工作：

- 建立 Project VSTO 增益集專案。

- 撰寫使用 Project 物件模型將工作加入新專案的程式碼。

- 建置和執行專案來進行測試。

- 清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] 或 [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案

### <a name="to-create-a-new-project-in-visual-studio"></a>在 Visual Studio 中建立新專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

3. 在範本窗格中，展開 [Visual C#] **Deploying Office Solutions** 或 [Visual Basic] ，然後展開 [Office/SharePoint] 。

4. 在展開的 [Office/SharePoint]  節點下，選取 [Office 增益集]  節點。

5. 在專案範本清單中，選取 [Project 2010 增益集]  或 [Project 2013 增益集] 。

6. 在 [名稱]  方塊中，輸入 **FirstProjectAddIn**。

7. 按一下 [確定]  。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會建立 **FirstProjectAddIn** 專案，並在編輯器中開啟 **ThisAddIn** 程式碼檔。

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>撰寫將新工作加入至專案的程式碼
 接著，將程式碼加入 ThisAddIn 程式碼檔。 新的程式碼會使用 Project 的物件模型將新工作加入專案。 根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：

- `ThisAddIn` 類別的部分定義。 這個類別提供您撰寫程式碼的進入點，並提供對 Project 物件模型的存取。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。類別的其餘部分 `ThisAddIn` 是在不應修改的隱藏程式碼檔案中定義。

- `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件處理常式。 當 Project 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在 VSTO 增益集卸載時清除它所用的資源。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

### <a name="to-add-a-task-to-a-new-project"></a>將工作加入新專案

1. 在 ThisAddIn 程式碼檔中，將下列程式碼加入 `ThisAddIn` 類別。 這段程式碼會定義 `Microsoft.Office.Interop.MSProject.Application` 類別之 `NewProject` 事件的事件處理常式。

    當使用者建立新專案時，這個事件處理常式會將工作加入專案。

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   若要修改專案，這個程式碼範例會使用下列物件：

- `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位會傳回 `Microsoft.Office.Interop.MSProject.Application` 物件，此物件代表 Project 目前的執行個體。

- `pj`NewProject 事件之事件處理常式的參數。 `pj` 參數是 `Microsoft.Office.Interop.MSProject.Project` 物件，此物件代表專案。 如需詳細資訊，請參閱 [專案方案](../vsto/project-solutions.md)。

1. 如果使用的是 C#，請將下列程式碼加入 `ThisAddIn_Startup` 事件處理常式中。 此程式碼會將 `Application_Newproject` 事件處理常式與 NewProject 事件連接。

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>測試專案
 當您建置並執行專案時，請確認新工作會出現在產生的新專案中。

### <a name="to-test-the-project"></a>測試專案

1. 按 **F5** 建置及執行專案。 Microsoft Project 會啟動並自動開啟新的空白專案。

     當您建置專案時，程式碼會編譯到包含在專案建置輸出資料夾中的組件。 Visual Studio 也會建立一組登錄項目，以便 Project 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。 如需詳細資訊，請參閱 [Office 方案組建流程總覽](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100))。

2. 確認新工作已加入空白專案。

3. 確認下列文字出現在工作的 [工作名稱]  欄位中。

     **This text was added by using code.**

4. 關閉 Microsoft Project。

## <a name="clean-up-the-project"></a>清除專案
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。 否則，每次在開發電腦上開啟 Microsoft Project 時，就會執行 VSTO 增益集。

### <a name="to-clean-up-your-project"></a>清除專案

1. 在 Visual Studio 中，按一下 [建置]  功能表上的 [清除方案] 。

## <a name="next-steps"></a>下一步
 現在您已經建立 Project 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：

- 您可以在 Project VSTO 增益集中執行的一般程式設計工作： [PROGRAM Vsto 增益集](../vsto/programming-vsto-add-ins.md)。

- 使用 Project 的物件模型： [專案方案](../vsto/project-solutions.md)。

- 建立和偵錯工具的 VSTO 增益集： [Build Office 方案](../vsto/building-office-solutions.md)。

- 部署 Project 的 VSTO 增益集： [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [專案解決方案](../vsto/project-solutions.md)
- [建立 Office 方案](../vsto/building-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [Office 專案範本總覽](../vsto/office-project-templates-overview.md)
