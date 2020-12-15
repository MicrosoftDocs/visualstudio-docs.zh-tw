---
title: 逐步解說：建立書簽的快捷方式功能表
description: 瞭解如何在 Microsoft Word 的檔層級自訂中建立書簽控制項的快捷方式功能表。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b018687ec10eb725ece7d776277ea1c699dbbec
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524222"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>逐步解說：建立書簽的快捷方式功能表
  本逐步解說示範如何 <xref:Microsoft.Office.Tools.Word.Bookmark> 在 Word 的檔層級自訂中建立控制項的快捷方式功能表。 當使用者以滑鼠右鍵按一下書簽中的文字時，會出現快捷方式功能表，並提供使用者選項來格式化文字。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 本逐步解說將說明下列工作：

- [建立專案](#BKMK_CreateProject)。

- [在檔中加入文字和書簽](#BKMK_addtextandbookmarks)。

- [將命令新增至快捷方式功能表](#BKMK_AddCmndsShortMenu)。

- [格式化書簽中的文字](#BKMK_formattextbkmk)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> 建立專案
 第一個步驟是在 Visual Studio 中建立 Word 檔專案。

### <a name="to-create-a-new-project"></a>建立新的專案

- 建立具有 [我的書簽名稱] **快捷方式功能表** 的 Word 檔專案。 在嚮導中，選取 [ **建立新檔**]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Word 檔，並將 [ **我的書簽] 快顯功能表** 專案加入 **方案總管**。

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> 將文字和書簽新增至檔
 在檔中新增一些文字，然後新增兩個重迭的書簽。

### <a name="to-add-text-to-your-document"></a>將文字加入檔

- 在專案設計工具中出現的檔中，輸入下列文字。

     **當您以滑鼠右鍵按一下書簽中的文字時，這就是建立快捷方式功能表的範例。**

### <a name="to-add-a-bookmark-control-to-your-document"></a>將書簽控制項新增至檔

1. 在 [ **工具箱**] 的 [ **Word 控制項** ] 索引標籤中，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項拖曳至檔。

    [ **加入書簽控制項** ] 對話方塊隨即出現。

2. 選取 [當您以滑鼠右鍵按一下文字時建立快捷方式功能表] 字樣，然後按一下 **[確定]**。

    `bookmark1` 會加入檔中。

3. 將另一個控制項新增至「以 <xref:Microsoft.Office.Tools.Word.Bookmark> 滑鼠右鍵按一下書簽中的文字」字樣。

    `bookmark2` 會加入檔中。

   > [!NOTE]
   > 和中的「以滑鼠右鍵按一下文字」字樣 `bookmark1` `bookmark2` 。

   當您在設計階段將書簽新增至檔時， <xref:Microsoft.Office.Tools.Word.Bookmark> 會建立控制項。 您可以針對書簽的數個事件進行程式設計。 您可以在書簽的事件中撰寫程式碼， <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> 當使用者以滑鼠右鍵按一下書簽中的文字時，就會出現快捷方式功能表。

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> 將命令新增至快捷方式功能表
 當您在檔上按一下滑鼠右鍵時，將按鈕新增至出現的快捷方式功能表。

### <a name="to-add-commands-to-a-shortcut-menu"></a>將命令新增至快捷方式功能表

1. 將 **功能區 XML** 專案加入至專案。 如需詳細資訊，請參閱 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

2. 在 **方案總管** 中，選取 [ **ThisDocument.cs** ] 或 [ **ThisDocument**]。

3. 在功能表列上，選擇 [**視圖** 程式  >  **代碼**]。

     **ThisDocument** 類別檔案隨即在程式碼編輯器中開啟。

4. 將下列程式碼加入至 **ThisDocument** 類別。 此程式碼會覆寫 CreateRibbonExtensibilityObject 方法，並將功能區 XML 類別傳回至 Office 應用程式。

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. 在方案總管 中選取功能區 XML 檔案。 根據預設，功能區 XML 檔名為 Ribbon1.xml。

6. 在功能表列上，選擇 [**視圖** 程式  >  **代碼**]。

     功能區 XML 檔案隨即在程式碼編輯器中開啟。

7. 在程式碼編輯器中，以下列程式碼取代功能區 XML 檔案的內容。

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     當您以滑鼠右鍵按一下檔時，此程式碼會將兩個按鈕新增至顯示的快捷方式功能表。

8. 在 **方案總管** 中，以滑鼠右鍵按一下 `ThisDocument` ，然後按一下 [視圖程式 **代碼**]。

9. 在類別層級宣告下列變數和書簽變數。

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. 在 **方案總管** 中，選取功能區程式碼檔案。 依預設，功能區程式碼檔的名稱為 **Ribbon1.cs** 或 **Ribbon1。**

11. 在功能表列上，選擇 [**視圖** 程式  >  **代碼**]。

     功能區程式碼檔案隨即在程式碼編輯器中開啟。

12. 在功能區程式碼檔案中，新增下列方法。 這是兩個按鈕的回呼方法，您已新增至檔的快捷方式功能表。 此方法會決定這些按鈕是否出現在快捷方式功能表中。 只有當您以滑鼠右鍵按一下書簽中的文字時，才會顯示粗體和斜體按鈕。

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> 格式化書簽中的文字

### <a name="to-format-the-text-in-the-bookmark"></a>格式化書簽中的文字

1. 在功能區程式碼檔案中，新增 `ButtonClick` 事件處理常式以將格式套用至書簽。

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **方案總管**，請選取 [ **ThisDocument.cs** ] 或 [ **ThisDocument**]。

3. 在功能表列上，選擇 [**視圖** 程式  >  **代碼**]。

     **ThisDocument** 類別檔案隨即在程式碼編輯器中開啟。

4. 將下列程式碼加入至 **ThisDocument** 類別。

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > 您必須撰寫程式碼來處理書簽重迭的情況。 如果您沒有這麼做，則預設會針對選取專案中的所有書簽呼叫程式碼。

5. 在 c # 中，您必須將書簽控制項的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>測試應用程式
 測試您的檔，確認當您以滑鼠右鍵按一下書簽中的文字，並將文字格式化時，快速鍵功能表中會出現粗體和斜體功能表項目。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 以滑鼠右鍵按一下第一個書簽，然後按一下 [ **粗體**]。

3. 確認中的所有文字 `bookmark1` 都格式化為粗體。

4. 以滑鼠右鍵按一下書簽重迭的文字，然後按一下 [ **斜體**]。

5. 確認中的所有文字 `bookmark2` 都是斜體，而且只有該重迭文字的部分 `bookmark1` `bookmark2` 是斜體。

## <a name="next-steps"></a>後續步驟
 接著可以執行下列一些工作：

- 撰寫程式碼以回應 Excel 中主控制項的事件。 如需詳細資訊，請參閱 [逐步解說：針對 NamedRange 控制項的事件進行程式](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)設計。

- 使用核取方塊可變更書簽中的格式。 如需詳細資訊，請參閱 [逐步解說：使用 CheckBox 控制項變更檔案格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。

## <a name="see-also"></a>另請參閱
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [書簽控制項](../vsto/bookmark-control.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
