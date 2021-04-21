---
title: 使用按鈕在工作表的文字方塊中顯示文字
description: 瞭解在 Microsoft Excel 工作表上使用按鈕和文字方塊的基本概念。 也可以使用 Visual Studio 中的 Office 開發工具來建立 Excel 專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827782"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>逐步解說：使用按鈕在工作表的文字方塊中顯示文字
  本逐步解說會示範在 Microsoft Office Excel 工作表上使用按鈕和文字方塊的基本概念，以及如何在 Visual Studio 中使用 Office 開發工具建立 Excel 專案。 若要以完整範例的形式查看結果，請參閱 [Office 開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Excel 控制項範例。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 將控制項新增至工作表。

- 按一下按鈕時填入文字方塊。

- 測試您的專案。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 在這個步驟中，您將使用 Visual Studio 建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 [ **我的 excel** 名稱] 按鈕建立 Excel 活頁簿專案。 確定已選取 [ **建立新檔** ]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的 Excel] 按鈕** 專案加入 **方案總管**。

## <a name="add-controls-to-the-worksheet"></a>將控制項新增至工作表
 針對這個逐步解說，您將需要第一個工作表上的按鈕和文字方塊。

### <a name="to-add-a-button-and-a-text-box"></a>新增按鈕和文字方塊

1. 確認 [ **我的 Excel Button.xlsx** ] 活頁簿已在 Visual Studio 設計工具中開啟，並 `Sheet1` 顯示。

2. 從 [工具箱] 的 [ **通用控制項** ] 索引標籤，將加入 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> 至 `Sheet1` 。

3. 從 [ **View** ] 功能表選取 [ **屬性視窗]**。

4. 在 [**屬性** 視窗] 下拉式清單方塊中，確定 **TextBox1** 可以看見，並將文字方塊的 [**名稱**] 屬性變更 **為 [顯示文字]**。

5. 將 **按鈕** 控制項拖曳至 `Sheet1` ，並變更下列屬性：

   |屬性|值|
   |--------------|-----------|
   |**名稱**|**insertText**|
   |**Text**|**插入文字**|

   現在，請撰寫按一下按鈕時要執行的程式碼。

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>按一下按鈕時填入文字方塊
 每次使用者按一下按鈕時， **Hello World！** 會附加至文字方塊。

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>在按一下按鈕時寫入至文字方塊

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **Sheet1**]，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 按鈕的事件處理常式：

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. 在 c # 中，您必須將事件處理常式加入至 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件，如下所示。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試活頁簿，以確保訊息 **Hello World！** 當您按一下按鈕時，會出現在文字方塊中。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按 **F5** 執行您的專案。

2. 按一下按鈕。

3. 確認 **Hello World！** 出現在文字方塊中。

## <a name="next-steps"></a>下一步
 本逐步解說顯示在 Excel 工作表上使用按鈕和文字方塊的基本概念。 接著可以執行下列一些工作：

- 部署專案。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

- 使用核取方塊變更格式。 如需詳細資訊，請參閱 [逐步解說：使用 CheckBox 控制項變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。

## <a name="see-also"></a>另請參閱
- [如何：將 Windows Forms 控制項新增至 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Office 檔上 Windows Forms 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
