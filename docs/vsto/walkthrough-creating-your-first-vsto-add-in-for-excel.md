---
title: 逐步解說：建立 Excel 的第一個 VSTO 增益集
description: 建立適用于 Microsoft Excel 的應用層級增益集。 不論開啟哪一份活頁簿，您所建立的功能都可用於應用程式本身。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fcb2bcc91eb1d19309904caae16701b814113089
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824402"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>逐步解說：建立 Excel 的第一個 VSTO 增益集
  本入門逐步解說將示範如何建立 Microsoft Office Excel 的應用程式層級增益集。 不論開啟哪一份活頁簿，您在這類方案中建立的功能都可供應用程式本身使用。

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 本逐步解說將說明下列工作：

- 建立 Excel 的 Excel VSTO 增益集專案。

- 撰寫可使用 Excel 物件模型的程式碼，儲存活頁簿時便可加入文字。

- 建置和執行專案來進行測試。

- 清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>在 Visual Studio 中建立新的 Excel VSTO 增益集專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

3. 在範本窗格中，展開 [Visual C#] **Deploying Office Solutions** 或 [Visual Basic] ，然後展開 [Office/SharePoint] 。

4. 在展開的 [Office/SharePoint]  節點下，選取 [Office 增益集]  節點。

5. 在專案範本清單中，選取 [Excel 2010 增益集] **Deploying Office Solutions** 或 [Excel 2013 增益集] 。

6. 在 [名稱] **Deploying Office Solutions** 方塊中，輸入 **FirstExcelAddIn**。

7. 按一下 [確定]  。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立 **FirstExcelAddIn** 專案，並在編輯器中開啟 ThisAddIn 程式碼檔案。

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>撰寫程式碼以將文字新增至儲存的活頁簿
 接著，將程式碼加入 ThisAddIn 程式碼檔。 新程式碼會使用 Excel 物件模型，將未定案文字插入現用工作表的第一列中。 現用工作表是使用者儲存活頁簿時所開啟的工作表。 根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：

- `ThisAddIn` 類別的部分定義。 這個類別提供您撰寫程式碼的進入點，並提供對 Excel 物件模型的存取。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。類別的其餘部分 `ThisAddIn` 是在不應修改的隱藏程式碼檔案中定義。

- `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件處理常式。 當 Excel 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在增益集卸載時清除它所用的資源。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>將一行文字加入儲存的活頁簿

1. 在 ThisAddIn 程式碼檔中，將下列程式碼加入 `ThisAddIn` 類別。 新的程式碼會定義 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 事件的事件處理常式，該事件是在儲存活頁簿時所引發的。

    當使用者儲存活頁簿時，事件處理常式會將新文字加入現用工作表開頭。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. 如果使用的是 C#，請將下列必要的程式碼加入 `ThisAddIn_Startup` 事件處理常式中。 這段程式碼是用來連接 `Application_WorkbookBeforeSave` 事件處理常式和 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 事件。

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   若要在儲存活頁簿時修改活頁簿，前面的程式碼範例可以使用下列物件：

- `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位會傳回 <xref:Microsoft.Office.Interop.Excel.Application> 物件，此物件代表 Excel 目前的執行個體。

- `Wb` 事件之事件處理常式的 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 參數。 `Wb` 參數是 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件，此物件代表儲存的活頁簿。 如需詳細資訊，請參閱 [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)。

## <a name="test-the-project"></a>測試專案

### <a name="to-test-the-project"></a>測試專案

1. 按 **F5** 建置及執行專案。

     當您建置專案時，程式碼會編譯到包含在專案建置輸出資料夾中的組件。 Visual Studio 也會建立一組登錄項目，以便 Excel 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。 如需詳細資訊，請參閱 [建立 Office 方案](../vsto/building-office-solutions.md)。

2. 在 Excel 中儲存活頁簿。

3. 請確認已將下列文字加入活頁簿。

     **This text was added by using code.**

4. 關閉 Excel。

## <a name="clean-up-the-project"></a>清除專案
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。 否則，每次在開發電腦上開啟 Excel 時，VSTO 增益集將會繼續執行。

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>清除開發電腦上已完成的專案

1. 在 Visual Studio 中，按一下 [建置]  功能表上的 [清除方案] 。

## <a name="next-steps"></a>下一步
 現在您已經建立 Excel 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：

- 您可以在 VSTO 增益集中執行的一般程式設計工作： [PROGRAM Vsto 增益集](../vsto/programming-vsto-add-ins.md)。

- Excel VSTO 增益集特有的程式設計工作： [excel 方案](../vsto/excel-solutions.md)。

- 使用 Excel 的物件模型： [excel 物件模型總覽](../vsto/excel-object-model-overview.md)。

- 自訂 Excel 的使用者介面 (UI) ，例如，將自訂索引標籤加入功能區，或建立您自己的自訂工作窗格： [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

- 建立和偵測 Excel 的 VSTO 增益集： [建立 Office 方案](../vsto/building-office-solutions.md)。

- 部署適用于 Excel 的 VSTO 增益集： [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel 方案](../vsto/excel-solutions.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [建立 Office 方案](../vsto/building-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [Office 專案範本總覽](../vsto/office-project-templates-overview.md)
