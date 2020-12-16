---
title: 逐步解說：使用 Windows Form 收集資料
description: 從 Microsoft Excel 的檔層級自訂中開啟 Windows Form、從使用者收集資訊，然後將該資訊寫入工作表儲存格。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58d6f58f732d4a52aade6ff3678842900f1c29cd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527172"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>逐步解說：使用 Windows Form 收集資料
  本逐步解說示範如何從 Microsoft Office Excel 的文件層級自訂開啟 Windows Form、向使用者收集資訊，以及將該資訊寫入工作表儲存格。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 雖然本逐步解說特別使用 Excel 的文件層級專案，但是所示範的概念也適用於其他 Office 專案。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="create-a-new-project"></a>建立新專案
 第一步是建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立名為 **WinFormInput** 的 Excel 活頁簿專案，然後選取精靈中的 [建立新文件]  。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 **WinFormInput** 專案加入方案總管 。

## <a name="add-a-namedrange-control-to-the-worksheet"></a>將 NamedRange 控制項新增至工作表

### <a name="to-add-a-named-range-to-sheet1"></a>將指定範圍加入 Sheet1

1. 選取 **上的儲存格** A1 `Sheet1`。

2. 在 [名稱]  方塊中，輸入 **formInput**。

     [名稱]  方塊位於工作表 **A** 欄正上方的公式列左側。

3. 按 **Enter**。

     <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項會加入儲存格 **A1**。 工作表上不會明顯表示，不過當選取儲存格 **A1** 時， **formInput** 會出現在 [名稱]  方塊 (工作表左上方) 和 [屬性]  視窗中。

## <a name="add-a-windows-form-to-the-project"></a>將 Windows Form 加入至專案
 建立 Windows Form 以提示使用者輸入資訊。

### <a name="to-add-a-windows-form"></a>加入 Windows Form

1. 在方案總管  中，選取專案 **WinFormInput**。

2. 在 [專案]  功能表上，按一下 [加入 Windows Form] 。

3. 將表單命名 **GetInputString.vb** 或 **GetInputString.cs**，然後按一下 [加入] 。

    新表單隨即在設計工具中開啟。

4. 將 <xref:System.Windows.Forms.TextBox> 和 <xref:System.Windows.Forms.Button> 加入表單。

5. 選取按鈕，在 [屬性]  視窗中找到 [文字]  屬性，然後將文字變更為 [確定] 。

   接下來，將程式碼加入 `ThisWorkbook.vb` 或 `ThisWorkbook.cs` ，以收集使用者的資訊。

## <a name="display-the-windows-form-and-collecting-information"></a>顯示 Windows Form 並收集資訊
 建立並顯示 `GetInputString` Windows Form 的執行個體，然後將使用者的資訊寫入工作表中的儲存格。

#### <a name="to-display-the-form-and-collect-information"></a>顯示表單並收集資訊

1. 以滑鼠右鍵按一下方案總管  中的 **ThisWorkbook.vb** 或 **ThisWorkbook.cs**，然後按一下 [檢視程式碼] 。

2. 在 <xref:Microsoft.Office.Tools.Excel.Workbook.Open> 的 `ThisWorkbook`事件處理常式，加入下列程式碼以宣告表單 `GetInputString` 的變數，然後顯示表單。

   > [!NOTE]
   > 在 C# 中，您必須加入事件處理常式，如以下 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件所示。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]

3. 建立名為 `WriteStringToCell` 的方法，以將文字寫入指定範圍。 系統會從表單呼叫這個方法，並將使用者的輸入傳遞至儲存格 <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 `formInput`上的 **控制項**。

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]

   接下來，將程式碼加入表單以處理按鈕的 Click 事件。

## <a name="send-information-to-the-worksheet"></a>將資訊傳送至工作表

### <a name="to-send-information-to-the-worksheet"></a>將資訊傳送至工作表

1. 以滑鼠右鍵按一下方案總管  中的 **GetInputString**，然後按一下 [檢視設計工具] 。

2. 按兩下這個按鈕，開啟已加入按鈕之 <xref:System.Windows.Forms.Control.Click> 事件處理常式的程式碼檔案。

3. 將程式碼加入事件處理常式，以便從文字方塊取得輸入、將輸入傳送至 `WriteStringToCell`函式，然後關閉表單。

     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]

## <a name="test"></a>測試
 您現在可以執行專案。 Windows Form 隨即出現，且您的輸入會出現在工作表中。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按 **F5** 執行您的專案。

2. 確認 Windows Form 隨即出現。

3. 在文字方塊中輸入 **Hello World** ，然後按一下 [確定] 。

4. 確認 **Hello World** 出現在工作表的儲存格 **A1** 中。

## <a name="next-steps"></a>後續步驟
 本逐步解說說明顯示 Windows Form 並將資料傳遞至工作表的基本概念。 您還可以執行下列其他工作：

- 使用 Excel 活頁簿或 Word 文件上的 Windows Form 控制項。 如需詳細資訊，請參閱 [Office 檔的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)。

- 從檔層級自訂或 VSTO 增益集修改 Microsoft Office 應用程式的使用者介面。 如需詳細資訊，請參閱 [OFFICE UI 自訂](../vsto/office-ui-customization.md)。

## <a name="see-also"></a>另請參閱
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
