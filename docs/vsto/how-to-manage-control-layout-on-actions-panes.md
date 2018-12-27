---
title: HOW TO：管理執行窗格控制項配置
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 38f9e534fe213b766ea74c83604ddf1cafa1ac65
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647045"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>HOW TO：管理執行窗格控制項配置
  執行窗格停駐文件或工作表的權限預設;不過，它可以停駐 left，top 或 bottom。 如果您使用多個使用者控制項，您可以撰寫程式碼，以適當堆疊使用者控制項，在 [動作] 窗格上。 如需詳細資訊，請參閱 <<c0> [ 執行窗格概觀](../vsto/actions-pane-overview.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 控制項堆疊順序取決於是否垂直或水平停駐 [動作] 窗格。  
  
> [!NOTE]  
>  如果使用者重新調整大小在執行階段的 [動作] 窗格，您可以設定來調整大小與執行窗格控制項。 您可以使用 Windows Form 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性，將控制項錨定到執行窗格。 如需詳細資訊，請參閱[＜How to：Windows Forms 上的控制項的錨點](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>若要設定執行窗格控制項堆疊順序  
  
1.  開啟包含具有多個使用者控制項或巢狀的執行窗格控制項的 [動作] 窗格的 Microsoft Office Word 的文件層級專案。 如需詳細資訊，請參閱[＜How to：加入執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
2.  以滑鼠右鍵按一下**ThisDocument.cs**或是**ThisDocument.vb**中**方案總管 中**然後按一下**檢視程式碼**。  
  
3.  在 [<xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>的動作] 窗格中，檢查 [動作] 窗格的方向是水平的事件處理常式。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  從左邊; 如果方向是水平的控制堆疊 [動作] 窗格否則，堆疊頂端。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  在 C# 中，您必須新增事件處理常式`ActionsPane`至<xref:Microsoft.Office.Tools.Word.Document.Startup>事件處理常式。 如需建立事件處理常式的資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  執行專案，並確認 [動作] 窗格停駐在文件中，頂端和 [動作] 窗格停駐在文件的右側時，會從上到下堆疊控制項時執行窗格控制項堆疊由左到右。  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Word 文件層級專案與包含多個使用者控制項的執行窗格或巢狀的執行窗格控制項。  
  
## <a name="see-also"></a>另請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何：執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：動作窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [逐步解說：從 [動作] 窗格中的文件中插入文字](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [逐步解說：從 [動作] 窗格中的文件中插入文字](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  