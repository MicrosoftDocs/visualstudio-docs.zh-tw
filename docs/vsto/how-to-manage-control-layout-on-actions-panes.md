---
title: 如何：管理執行窗格的控制項版面配置
description: 瞭解如何藉由撰寫程式碼來適當地堆疊使用者控制項，來管理動作窗格上的控制項版面配置。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49739b6011fcf977db84a3350929a56514040975
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918584"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>如何：管理執行窗格的控制項版面配置
  執行窗格預設會停駐在檔或工作表的右側;不過，它可以停駐在左邊、頂端或底部。 如果您使用多個使用者控制項，您可以撰寫程式碼，在 [動作] 窗格上適當地堆疊使用者控制項。 如需詳細資訊，請參閱執行 [窗格總覽](../vsto/actions-pane-overview.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 控制項的堆疊順序取決於 [動作] 窗格是垂直或水準固定。

> [!NOTE]
> 如果使用者在執行時間調整執行窗格的大小，您可以使用 [執行] 窗格，將控制項設定為調整大小。 您可以使用 Windows Form 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性，將控制項錨定到執行窗格。 如需詳細資訊，請參閱 [如何：錨定 Windows Forms 上的控制項](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>設定執行窗格控制項的堆疊順序

1. 開啟 Microsoft Office Word 的檔層級專案，其中包含具有多個使用者控制項或嵌套動作窗格控制項的執行窗格。 如需詳細資訊，請參閱 [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。

2. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ThisDocument.cs** ] 或 [ **ThisDocument** ]，然後按一下 [**視圖程式碼**]。

3. 在 <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> [動作] 窗格的 [事件處理常式] 中，檢查 [動作] 窗格的方向是否為水準。

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. 如果方向為水準，請從左邊堆疊動作窗格控制項;否則，請從頂端堆疊它們。

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. 在 c # 中，您必須將的事件處理常式加入 `ActionsPane` 至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件處理常式。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. 執行專案並確認 [動作] 窗格控制項在檔頂端停駐時，由左至右堆疊，當執行窗格停駐在檔的右側時，控制項就會從上到下堆疊。

## <a name="example"></a>範例
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 包含執行窗格的 Word 檔層級專案，其中包含多個使用者控制項或嵌套的執行窗格控制項。

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [逐步解說：從執行窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [逐步解說：從執行窗格將文字插入檔](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
