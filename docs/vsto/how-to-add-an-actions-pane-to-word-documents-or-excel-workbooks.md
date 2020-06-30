---
title: 將執行窗格新增至 Word 檔或 Excel 活頁簿
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2d24ec3a17c9e0824c6b7aaffeaaac02c1c4f76e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546220"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>如何：將執行窗格加入至 Word 文件或 Excel 活頁簿
  若要將執行窗格加入至 Microsoft Office Word 檔或 Microsoft Excel 活頁簿，請先建立 Windows Forms 的使用者控制項。 然後，將使用者控制項加入至 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` 專案中欄位（Word）或 `ThisWorkbook.ActionsPane` 欄位（Excel）的屬性。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="creating-the-user-control"></a>建立使用者控制項
 下列程式顯示如何在 Word 或 Excel 專案中建立使用者控制項。 它也會將按鈕加入至使用者控制項，以在按一下時將文字寫入檔或活頁簿。

#### <a name="to-create-the-user-control"></a>若要建立使用者控制項

1. 在 Visual Studio 中開啟 Word 或 Excel 檔層級專案。

2. 在 [專案]**** 功能表上，按一下 [加入新項目]****。

3. 在 [**加入新專案**] 對話方塊中，選取 [**動作] 窗格控制項**，將它命名為**HelloControl**，然後按一下 [**新增**]。

    > [!NOTE]
    > 或者，您也可以將**使用者控制項**專案加入至您的專案。 執行**窗格控制項**和**使用者控制項**專案所產生的類別在功能上是相同的。

4. 從 [工具箱] 的 [ **Windows Forms** ] 索引標籤**中，** 將 [**按鈕**] 控制項拖曳至控制項上。

    > [!NOTE]
    > 如果在設計工具中看不到控制項，請按兩下**方案總管**中的 [ **HelloControl** ]。

5. 將程式碼加入至 <xref:System.Windows.Forms.Control.Click> 按鈕的事件處理常式。 下列範例會顯示 Microsoft Office Word 檔的程式碼。

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. 在 c # 中，您必須加入按一下按鈕的事件處理常式。 呼叫之後，您可以將此程式碼放在函式中 `HelloControl` `InitializeComponent` 。

     如需如何建立事件處理常式的詳細資訊，請參閱[如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>將使用者控制項新增至 [動作] 窗格
 若要顯示 [動作] 窗格，請將使用者控制項加入至 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` 欄位（Word）或 `ThisWorkbook.ActionsPane` 欄位（Excel）的屬性。

### <a name="to-add-the-user-control-to-the-actions-pane"></a>將使用者控制項新增至 [動作] 窗格

1. 將下列程式碼新增至 `ThisDocument` 或 `ThisWorkbook` 類別，做為類別層級宣告（請勿將此程式碼新增至方法）。

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. 將下列程式碼新增至 `ThisDocument_Startup` 類別的事件處理常式 `ThisDocument` 或 `ThisWorkbook_Startup` 類別的事件處理常式 `ThisWorkbook` 。

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [逐步解說：從執行窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [如何：管理動作窗格上的控制項版面配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [逐步解說：從執行窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
