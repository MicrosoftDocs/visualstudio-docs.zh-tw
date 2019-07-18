---
title: 變更文件格式使用核取方塊控制項
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
ms.openlocfilehash: 24c3cb8d76551bb477f9c13cc56c313519f3b617
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328730"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>逐步解說：變更文件格式使用核取方塊控制項
  本逐步解說示範如何使用 Microsoft Office Word 文件層級自訂中的 Windows Form 控制項，來變更文字格式。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 這個逐步解說將說明下列工作：

- 文字和控制項加入文件的文件層級專案在設計階段加入。

- 在選取的選項，請格式化的文字。

  若要查看完整的範例結果，請參閱 Word 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 第一個步驟是建立 Windows 文件專案。

### <a name="create-a-new-project"></a>建立新專案

1. 建立 Word 文件專案名稱**My Word 格式設定**。 在精靈中，選取**建立新的文件**。

     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 設計工具中開啟新的 Word 文件，並將**My Word 格式設定**專案加入**方案總管 中**。

## <a name="add-text-and-controls-to-the-word-document"></a>將文字和控制項加入 Word 文件
 對於此逐步解說中，加入三個核取方塊和中的某些文字<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入 Word 文件。 核取方塊將呈現給使用者的選項，格式化文字。

### <a name="add-three-check-boxes"></a>新增三個核取方塊

1. 請確認已在 Visual Studio 設計工具中開啟文件。

2. 從**通用控制項**索引標籤**工具箱**，將第一個<xref:Microsoft.Office.Tools.Word.Controls.CheckBox>文件的控制項。

3. 在 [屬性]  視窗中變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyBoldFont**|
    |**Text**|**粗體**|

4. 按下**Enter**移動第一個核取方塊下方的插入點。

5. 加入下列文件中的第二個核取方塊`ApplyBoldFont`核取方塊，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyItalicFont**|
    |**Text**|**斜體**|

6. 按下**Enter**將第二個核取方塊下方的插入點。

7. 加入下列文件中的第三個核取方塊`ApplyItalicFont`核取方塊，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyUnderlineFont**|
    |**Text**|**加上底線**|

### <a name="add-text-and-a-bookmark-control"></a>加入文字和書籤控制項

1. 將游標移到核取方塊控制項下方，輸入下列文字：

    **按一下核取方塊以變更這段文字格式。**

2. 從**Word 控制項**索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Word.Bookmark>文件的控制項。

    **加入書籤控制項** 對話方塊隨即出現。

3. 選取您加入至文件的文字，然後按一下**確定**。

    A<xref:Microsoft.Office.Tools.Word.Bookmark>控制項，名為**Bookmark1**加入至文件中選取的文字。

4. 在 [**屬性**] 視窗中，變更的值 **（名稱）** 屬性設**fontText。**

   接下來，撰寫程式碼格式化的文字，當您核取或清除核取方塊時。

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>當您核取或清除核取方塊時，格式化文字
 當使用者選取一個格式化選項，變更文件中文字的格式。

### <a name="change-formatting-when-a-check-box-is-selected"></a>時已選取核取方塊變更格式

1. 以滑鼠右鍵按一下`ThisDocument`中**方案總管 中**，然後按一下**檢視程式碼**快顯功能表。

2. 針對C#，請將下列常數，以便**ThisDocument**類別。

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyBoldFont`核取方塊。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyItalicFont`核取方塊。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyUnderlineFont`核取方塊。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. 在C#，您必須新增到文字方塊中的事件處理常式<xref:Microsoft.Office.Tools.Word.Document.Startup>事件。 如需有關如何建立事件處理常式的資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試您的文件，以確認您選取或清除核取方塊時，文字會正確地格式化。

### <a name="test-your-document"></a>測試您的文件

1. 按下**F5**執行您的專案。

2. 選取或清除核取方塊。

3. 請確認文字的格式正確。

## <a name="next-steps"></a>後續步驟
 本逐步解說會示範使用核取方塊，並以程式設計方式變更文字格式設定 Word 文件上的基本概念。 接著可以執行下列一些工作：

- 使用按鈕填入文字方塊。 如需詳細資訊，請參閱[逐步解說：使用按鈕文件中的文字方塊中顯示的文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。

- 使用選項按鈕以選取圖表樣式。 如需詳細資訊，請參閱[逐步解說：更新使用選項按鈕的文件中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 文件上的 Windows Form 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
