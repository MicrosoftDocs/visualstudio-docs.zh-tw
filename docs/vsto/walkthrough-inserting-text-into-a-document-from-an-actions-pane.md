---
title: 逐步解說：從執行窗格將文字插入檔
description: 在 Microsoft Word 檔中建立執行窗格。 瞭解 [執行] 窗格包含兩個可收集輸入，然後將文字傳送至檔的控制項。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1ac42954e32b30a293abbe031218213948fb103a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824974"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>逐步解說：從執行窗格將文字插入檔
  本逐步解說示範如何在 Microsoft Office Word 檔中建立執行窗格。 [動作] 窗格包含兩個可收集輸入的控制項，然後將文字傳送至檔。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 本逐步解說將說明下列工作：

- 使用動作窗格控制項上的 Windows Forms 控制項來設計介面。

- 當應用程式開啟時顯示 [動作] 窗格。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 第一個步驟是建立 Windows 文件專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 [ **我的基本動作] 窗格** 建立 Word 檔專案。 在嚮導中，選取 [ **建立新檔**]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Word 檔，並將 [ **我的基本動作] 窗格** 專案加入 **方案總管**。

## <a name="add-text-and-bookmarks-to-the-document"></a>將文字和書簽新增至檔
 [動作] 窗格會將文字傳送至檔中的書簽。 若要設計檔，請輸入一些文字來建立基本的表單。

### <a name="to-add-text-to-your-document"></a>將文字加入檔

1. 在 Word 檔中輸入下列文字：

    **2008年3月21日**

    **名稱**

    **位址**

    **這是 Word 中的基本動作窗格範例。**

   您可以將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項從 [ **工具箱** ] 中的 [Visual Studio] 中拖曳，或使用 Word 中的 [ **書簽** ] 對話方塊，將控制項加入檔。

### <a name="to-add-a-bookmark-control-to-your-document"></a>將書簽控制項新增至檔

1. 從 [**工具箱**] 的 [ **Word 控制項**] 索引標籤，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項拖曳至檔。

     [ **加入書簽控制項** ] 對話方塊隨即出現。

2. 選取 [單字 **名稱**]，但不選取段落標記，然後按一下 **[確定]**。

    > [!NOTE]
    > 段落標記應該在書簽之外。 如果檔中沒有顯示段落標記，請按一下 [ **工具** ] 功能表，指向 [ **Microsoft Office Word 工具** ]，然後按一下 [ **選項**]。 按一下 [**流覽**] 索引標籤，然後在 [**選項**] 對話方塊的 [**格式化標示**] 區段中，選取 [**段落標記**] 核取方塊。

3. 在 [**屬性**] 視窗中，將 **Bookmark1** 的 **Name** 屬性變更為 **showName**。

4. 選取 [單字 **位址**]，而不選取段落標記。

5. 在功能區的 [ **插入** ] 索引標籤上，按一下 [ **連結** ] 群組中的 [ **書簽**]。

6. 在 [**書簽**] 對話方塊中，于 [**書簽名稱**] 方塊中輸入 **ShowAddress** ，然後按一下 [**新增**]。

## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格
 若要設計執行窗格介面，請在專案中加入 [執行] 窗格控制項，然後將 Windows Forms 控制項加入至 [動作] 窗格控制項。

### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項

1. 在 **方案總管** 中選取 [**我的基本動作] 窗格** 專案。

2. 在 [專案] 功能表上，按一下 [加入新項目]。

3. 在 [ **加入新專案** ] 對話方塊中，按一下 [ **動作] 窗格控制項**，將控制項命名為 **InsertTextControl，** 然後按一下 [ **加入**]。

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>若要將 Windows Form 控制項加入至執行窗格控制項

1. 如果在設計工具中看不到 [動作] 窗格控制項，請按兩下 [ **InsertTextControl**]。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 [**標籤**] 控制項拖曳至 [動作] 窗格控制項。

3. 將 [標籤] 控制項的 [ **文字** ] 屬性變更為 [ **名稱**]。

4. 將 **Textbox** 控制項新增至執行窗格控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**getName**|
    |**大小**|**130, 20**|

5. 將第二個 **標籤** 控制項新增至 [執行] 窗格控制項，並將 [ **Text** ] 屬性變更為 [ **Address**]。

6. 將第二個 **Textbox** 控制項新增至執行窗格控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**getAddress**|
    |**接受 Return**|**True**|
    |**多行**|**True**|
    |**大小**|**130, 40**|

7. 將 **按鈕** 控制項新增至執行窗格控制項，並變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**Shapes.addtext**|
    |**Text**|**插入**|

## <a name="add-code-to-insert-text-into-the-document"></a>新增程式碼以將文字插入檔中
 在 [動作] 窗格中，撰寫程式碼，將文字方塊中的文字插入 <xref:Microsoft.Office.Tools.Word.Bookmark> 檔中的適當控制項。 您可以使用 `Globals` 類別，從 [動作] 窗格上的控制項存取檔上的控制項。 如需詳細資訊，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>若要從檔中的書簽插入 [動作] 窗格中的文字

1. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> [ **shapes.addtext** ] 按鈕的事件處理常式。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. 在 c # 中，您必須加入按一下按鈕的事件處理常式。 在呼叫之後，您可以將此程式碼放在函式中 `InsertTextControl` `InitializeComponent` 。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>加入程式碼以顯示 [動作] 窗格
 若要顯示 [執行] 窗格，請將您建立的控制項加入至控制項集合。

### <a name="to-show-the-actions-pane"></a>顯示動作窗格

1. 在類別中建立執行窗格控制項的新實例 `ThisDocument` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. 將下列程式碼加入至的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件處理常式 `ThisDocument` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>測試應用程式
 測試您的檔，以確認開啟檔時，[動作] 窗格會開啟，並在按下按鈕時，將輸入文字方塊的文字插入書簽中。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 確認 [動作] 窗格是可見的。

3. 在 [動作] 窗格的文字方塊中輸入您的名稱和位址，然後按一下 [ **插入**]。

## <a name="next-steps"></a>下一步
 接著可以執行下列一些工作：

- 在 Excel 中建立執行窗格。 如需詳細資訊，請參閱 [如何：將執行窗格加入至 Excel 活頁簿](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))。

- 將資料系結至執行窗格上的控制項。 如需詳細資訊，請參閱 [逐步解說：將資料系結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [如何：將執行窗格加入至 Excel 活頁簿](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [如何：管理執行窗格的控制項版面配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [書簽控制項](../vsto/bookmark-control.md)
