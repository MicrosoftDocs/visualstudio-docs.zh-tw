---
title: 使用 CheckBox 控制項變更檔案格式
description: 瞭解如何在 Microsoft Word 的檔層級自訂中使用 Windows Forms 控制項來變更文字格式。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 931e9554a10e0e1525d9ee4a10505633b211610b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527250"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>逐步解說：使用 CheckBox 控制項變更檔案格式
  本逐步解說示範如何在 Microsoft Office Word 的檔層級自訂中使用 Windows Forms 控制項，以變更文字格式。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 本逐步解說將說明下列工作：

- 在檔層級專案中，于設計階段將文字和控制項加入檔。

- 選取選項時將文字格式化。

  若要以完整範例的形式查看結果，請參閱 [Office 開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Word 控制項範例。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 第一個步驟是建立 Windows 文件專案。

### <a name="create-a-new-project"></a>建立新專案

1. 使用 [ **我的單字格式**] 名稱建立 word 檔專案。 在嚮導中，選取 [ **建立新檔**]。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Word 檔，並將 [ **我的 Word 格式** ] 專案加入 **方案總管**。

## <a name="add-text-and-controls-to-the-word-document"></a>將文字和控制項新增至 Word 檔
 在這個逐步解說中，將控制項中的三個核取方塊和一些文字加入 <xref:Microsoft.Office.Tools.Word.Bookmark> Word 檔中。 核取方塊會向使用者呈現格式化文字的選項。

### <a name="add-three-check-boxes"></a>新增三個核取方塊

1. 請確認已在 Visual Studio 設計工具中開啟文件。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將第一個 <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> 控制項拖曳至檔。

3. 在 [屬性]  視窗中變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyBoldFont**|
    |**Text**|**粗體字**|

4. 按 **enter** 鍵，將插入點移到第一個核取方塊下方。

5. 將第二個核取方塊加入核取方塊下方的檔 `ApplyBoldFont` ，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyItalicFont**|
    |**Text**|**斜體**|

6. 按 **enter** 鍵，將插入點移到第二個核取方塊下方。

7. 將第三個核取方塊新增至核取方塊下方的檔 `ApplyItalicFont` ，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyUnderlineFont**|
    |**Text**|**Underline**|

### <a name="add-text-and-a-bookmark-control"></a>新增文字和書簽控制項

1. 將插入點移到核取方塊控制項下方，然後輸入下列文字：

    **按一下核取方塊，即可變更此文字的格式。**

2. 從 [**工具箱**] 的 [ **Word 控制項**] 索引標籤，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項拖曳至檔。

    [ **加入書簽控制項** ] 對話方塊隨即出現。

3. 選取您新增至檔的文字，然後按一下 **[確定]**。

    <xref:Microsoft.Office.Tools.Word.Bookmark>名為 **Bookmark1** 的控制項會加入至檔中選取的文字。

4. 在 [ **屬性** ] 視窗中，將 [ **(名稱)** ] 屬性的值變更為 **fontText。**

   接下來，撰寫程式碼，以在核取或清除核取方塊時格式化文字。

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>核取或清除核取方塊時格式化文字
 當使用者選取格式化選項時，請變更檔中文字的格式。

### <a name="change-formatting-when-a-check-box-is-selected"></a>選取核取方塊時變更格式

1. 以滑鼠右鍵 `ThisDocument` 按一下 **方案總管**，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 若僅限 c #，請將下列常數加入至 **ThisDocument** 類別。

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 核取方塊的事件處理常式 `applyBoldFont` 。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 核取方塊的事件處理常式 `applyItalicFont` 。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 核取方塊的事件處理常式 `applyUnderlineFont` 。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. 在 c # 中，您必須將文字方塊的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。 如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試檔案，以確認當您選取或清除核取方塊時，文字的格式是否正確。

### <a name="test-your-document"></a>測試您的檔

1. 按 **F5** 執行您的專案。

2. 選取或清除核取方塊。

3. 確認文字的格式正確。

## <a name="next-steps"></a>後續步驟
 本逐步解說將示範如何使用核取方塊，並以程式設計方式變更 Word 檔的文字格式。 接著可以執行下列一些工作：

- 使用按鈕來填入文字方塊。 如需詳細資訊，請參閱 [逐步解說：使用按鈕在檔的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。

- 使用選項按鈕以選取圖表樣式。 如需詳細資訊，請參閱 [逐步解說：使用選項按鈕更新檔中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 檔上 Windows Forms 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
