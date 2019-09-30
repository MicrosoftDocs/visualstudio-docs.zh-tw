---
title: HOW TO：管理動作窗格上的控制項版面配置
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 043f93c12181d34e9d2a92435c854cdf76f18904
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255817"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>作法：管理動作窗格上的控制項版面配置
  [動作] 窗格預設會停駐在檔或工作表的右側;不過，它可以停駐在左側、頂端或底部。 如果您使用多個使用者控制項，您可以撰寫程式碼，適當地堆疊 [動作] 窗格上的使用者控制項。 如需詳細資訊，請參閱[動作窗格總覽](../vsto/actions-pane-overview.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 控制項的堆疊順序取決於 [動作] 窗格是以垂直或水準方式停駐。

> [!NOTE]
> 如果使用者在執行時間調整 [動作] 窗格的大小，您可以使用 [動作] 窗格設定控制項的大小。 您可以使用 Windows Form 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性，將控制項錨定到執行窗格。 如需詳細資訊，請參閱[如何：Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)上的錨定控制項。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>若要設定執行窗格控制項的堆疊順序

1. 開啟包含具有多個使用者控制項或嵌套執行窗格控制項之 [動作] 窗格的 Microsoft Office Word 檔層級專案。 如需詳細資訊，請參閱[如何：將執行窗格新增至 Word 檔或 Excel 活頁](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)簿。

2. 以滑鼠右鍵按一下**方案總管**中的 [ **ThisDocument.cs** ] 或 [ **ThisDocument** ]，然後按一下 [**查看程式碼**]。

3. 在 [ <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>動作] 窗格的事件處理常式中，檢查 [動作] 窗格的方向是否為 [水準]。

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. 如果方向是水準的，則從左側堆疊 [動作窗格] 控制項;否則，請從頂端將它們堆疊。

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. 在C#中，您必須將的`ActionsPane`事件處理常式加入至<xref:Microsoft.Office.Tools.Word.Document.Startup>事件處理常式。 如需建立事件處理常式的詳細[資訊，請參閱如何：在 Office 專案](../vsto/how-to-create-event-handlers-in-office-projects.md)中建立事件處理常式。

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. 執行專案，並確認當 [動作] 窗格停駐在檔最上方時，[動作] 窗格控制項是從左至右堆疊，而當 [動作] 窗格停駐在檔的右邊時，控制項會從上到下堆疊。

## <a name="example"></a>範例
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 具有 [動作] 窗格的 Word 檔層級專案，其中包含多個使用者控制項或嵌套的動作窗格控制項。

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [如何：將執行窗格新增至 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [如何：將執行窗格新增至 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [逐步解說：從 [動作] 窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [逐步解說：從 [動作] 窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
