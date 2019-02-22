---
title: 逐步解說：建立書籤的捷徑功能表
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
ms.openlocfilehash: fb09bc2ee3f9278026be2046ff249fb2ca4c558f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863990"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>逐步解說：建立書籤的捷徑功能表
  本逐步解說示範如何建立捷徑功能表<xref:Microsoft.Office.Tools.Word.Bookmark>Word 文件層級自訂中的控制項。 當使用者以滑鼠右鍵按一下書籤中的文字時，快顯功能表會隨即出現，並提供格式化文字的使用者選項。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
- [建立專案](#BKMK_CreateProject)。  
  
- [加入文件中的文字和書籤](#BKMK_addtextandbookmarks)。  
  
- [將命令加入至捷徑功能表](#BKMK_AddCmndsShortMenu)。  
  
- [格式化文字方塊中的書籤](#BKMK_formattextbkmk)。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> 建立專案  
 第一個步驟是在 Visual Studio 中建立 Word 文件專案。  
  
### <a name="to-create-a-new-project"></a>建立新的專案  
  
-   建立具有名稱的 Word 文件專案**我的書籤快顯功能表**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱[＜How to：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**我的書籤快顯功能表**專案加入**方案總管 中**。  
  
##  <a name="BKMK_addtextandbookmarks"></a> 加入文件中的文字和書籤  
 您的文件中加入一些文字，並新增兩個重疊書籤。  
  
### <a name="to-add-text-to-your-document"></a>將文字加入文件  
  
-   在文件出現在您的專案設計工具中，輸入下列文字。  
  
     **這是建立快顯功能表，當您以滑鼠右鍵按一下 書籤文字的範例。**  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>若要加入書籤控制項加入文件  
  
1. 在 **工具箱**，從**Word 控制項**索引標籤，拖曳<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件。  
  
    **加入書籤控制項** 對話方塊隨即出現。  
  
2. 選取 「 文字上按一下滑鼠右鍵時，請建立快顯功能表 」 的文字，然後按一下**確定**。  
  
    `bookmark1` 會加入至文件。  
  
3. 新增另一個<xref:Microsoft.Office.Tools.Word.Bookmark>控制字組 」 以滑鼠右鍵按一下書籤中的文字 」。  
  
    `bookmark2` 會加入至文件。  
  
   > [!NOTE]  
   >  "以滑鼠右鍵按一下文字 」 會在單字`bookmark1`和`bookmark2`。  
  
   當您在設計階段新增至文件書籤<xref:Microsoft.Office.Tools.Word.Bookmark>建立控制項。 您可以針對數個事件的書籤程式。 您可以撰寫程式碼<xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>事件的書籤，以便當使用者按一下滑鼠右鍵在書籤，文字會出現捷徑功能表。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> 將命令加入至捷徑功能表  
 將按鈕加入至您以滑鼠右鍵按一下 文件時，會出現快顯功能表。  
  
### <a name="to-add-commands-to-a-shortcut-menu"></a>若要將命令加入至捷徑功能表  
  
1.  新增**功能區 XML**項目加入專案。 如需詳細資訊，請參閱[＜How to：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在 **方案總管**，選取**ThisDocument.cs**或是**ThisDocument.vb**。  
  
3.  在功能表列上依序選擇 [檢視] > [程式碼]。  
  
     **ThisDocument**類別檔案會開啟在程式碼編輯器。  
  
4.  將下列程式碼加入**ThisDocument**類別。 此程式碼會覆寫 CreateRibbonExtensibilityObject 方法和功能區 XML 類別傳回 Office 應用程式。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  在方案總管 中選取功能區 XML 檔案。 根據預設，功能區 XML 檔名為 Ribbon1.xml。  
  
6.  在功能表列上依序選擇 [檢視] > [程式碼]。  
  
     功能區 XML 檔案隨即在程式碼編輯器中開啟。  
  
7.  在程式碼編輯器中，會取代下列程式碼中的功能區 XML 檔案的內容。  
  
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
  
     此程式碼會將您以滑鼠右鍵按一下 文件時，會出現快顯功能表中的兩個按鈕。  
  
8.  在 [**方案總管] 中**，以滑鼠右鍵按一下`ThisDocument`，然後按一下**檢視程式碼**。  
  
9. 宣告下列變數和書籤變數在類別層級。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. 在 **方案總管 中**，選取 功能區程式碼檔案。 根據預設，功能區程式碼檔案名**Ribbon1.cs**或是**Ribbon1.vb**。  
  
11. 在功能表列上依序選擇 [檢視] > [程式碼]。  
  
     功能區程式碼檔案隨即在程式碼編輯器中開啟。  
  
12. 在功能區程式碼檔案中，新增下列方法。 這是您已加入文件的捷徑功能表的兩個按鈕的回呼方法。 這個方法會判斷在快顯功能表是否顯示這些按鈕。 只有當您以滑鼠右鍵按一下 書籤內的文字，則會出現粗體和斜體按鈕。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> 格式化文字方塊中的書籤  
  
### <a name="to-format-the-text-in-the-bookmark"></a>若要格式化文字方塊中的書籤  
  
1.  在功能區程式碼檔案中，新增`ButtonClick`將格式套用至書籤的事件處理常式。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **方案總管**，選取**ThisDocument.cs**或是**ThisDocument.vb**。  
  
3.  在功能表列上依序選擇 [檢視] > [程式碼]。  
  
     **ThisDocument**類別檔案會開啟在程式碼編輯器。  
  
4.  將下列程式碼加入**ThisDocument**類別。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  您必須撰寫程式碼，以處理重疊書籤的情況。 如果沒有這樣做，依預設，程式碼就會呼叫選取範圍中的所有書籤。  
  
5.  在 C# 中，您必須加入書籤控制項的事件處理常式<xref:Microsoft.Office.Tools.Word.Document.Startup>事件。 如需建立事件處理常式的資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="test-the-application"></a>測試應用程式  
 測試文件，以確認當您以滑鼠右鍵按一下 書籤文字粗體和斜體的功能表項目將會出現快顯功能表中，而且已正確格式化的文字。  
  
### <a name="to-test-your-document"></a>測試文件  
  
1.  按下**F5**執行您的專案。  
  
2.  在第一個書籤，以滑鼠右鍵按一下，然後按一下**粗體**。  
  
3.  確認所有的文字中`bookmark1`格式化為粗體。  
  
4.  以滑鼠右鍵按一下的文字個重疊書籤，然後按一下**斜體**。  
  
5.  確認所有中的文字`bookmark2`是斜體，並只中文字的一部分`bookmark1`重疊`bookmark2`為斜體。  
  
## <a name="next-steps"></a>後續步驟  
 接著可以執行下列一些工作：  
  
-   撰寫程式碼以回應在 Excel 中的主控制項的事件。 如需詳細資訊，請參閱[逐步解說：針對 NamedRange 控制項的事件的程式](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)。  
  
-   若要變更書籤中的格式使用核取方塊。 如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項變更文件格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [書籤控制項](../vsto/bookmark-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
