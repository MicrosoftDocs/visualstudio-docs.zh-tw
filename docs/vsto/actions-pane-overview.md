---
title: "執行窗格概觀 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
ms.assetid: 1b9b7db5-b19f-44ea-a774-f0962ca03bd2
caps.latest.revision: "101"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b03d391917bb472b8b7c1780942c8259562a633
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="actions-pane-overview"></a>執行窗格概觀
  執行窗格是可自訂**文件動作**附加到特定的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿的工作窗格。 例如，裝載在 Office 工作窗格，以及其他內建工作窗格內**XML 來源**在 Excel 中的工作窗格或**樣式與格式**Word 工作窗格。 您可以使用 Windows Form 控制項或 WPF 控制項，設計執行窗格使用者介面。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以只為 Word 或 Excel 建立文件層級自訂的執行窗格。 您無法在 VSTO 增益集中建立執行窗格。 如需詳細資訊，請參閱 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
> [!NOTE]  
>  執行窗格與自訂工作窗格不同。 自訂工作窗格是與應用程式相關聯，而非特定的文件。 您可以為某些 Microsoft Office 應用程式，在 VSTO 增益集中建立自訂工作窗格。 如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何執行 i： 使用 WPF 控制項內 Excel 執行窗格？](http://go.microsoft.com/fwlink/?LinkId=132763)。  
  
## <a name="displaying-the-actions-pane"></a>顯示執行窗格  
 執行窗格由 <xref:Microsoft.Office.Tools.ActionsPane> 類別代表。 當您建立文件層級專案時，在專案中使用 `ThisWorkbook` 類別 (Excel) 或 `ThisDocument` 類別 (Word) 的 `ActionsPane` 欄位，就可在程式碼中使用這個類別的執行個體。 若要顯示執行窗格，請將 Windows Form 控制項加入 `ActionsPane` 欄位的 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 屬性。 下列程式碼範例會將名為 `actions` 的控制項加入執行窗格。  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
 只要明確地將控制項加入執行窗格，就可在執行階段顯示執行窗格。 當執行窗格出現後，您可以動態加入或移除控制項，以回應使用者的動作。 一般而言，加入程式碼是為了在 `ThisDocument` 或 `ThisWorkbook` 的 `Startup` 事件處理常式中顯示執行窗格，讓使用者第一次開啟文件時即看見執行窗格。 不過，您可能希望執行窗格只在回應文件中的使用者動作時才出現。 例如，您可能會在文件的控制項 `Click` 事件中加入程式碼。  
  
### <a name="adding-multiple-controls-to-the-actions-pane"></a>將多個控制項加入執行窗格  
 如果要在執行窗格中加入多個控制項，在大部分情況下您應該將這些控制項聚集成一個使用者控制項，然後將這個使用者控制項加入 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 屬性。 這個程序包括下列步驟：  
  
1.  建立動作 窗格中的使用者介面 (UI)，藉由新增**執行窗格控制項**或**使用者控制項**至您的專案項目。 這兩個項目都包含自訂的 Windows Form <xref:System.Windows.Forms.UserControl> 類別。 **執行窗格控制項**和**使用者控制項**是相等的項目; 唯一的差別僅在於名稱。  
  
2.  使用設計工具或撰寫程式碼，將 Windows Form 控制項加入 <xref:System.Windows.Forms.UserControl>。  
  
    > [!NOTE]  
    >  您也可以藉由將 WPF <xref:System.Windows.Controls.UserControl> 加入 Windows Form <xref:System.Windows.Forms.UserControl>，在執行窗格中加入 WPF 控制項。 如需詳細資訊，請參閱[Office 方案中使用 WPF 控制項](../vsto/using-wpf-controls-in-office-solutions.md)。  
  
3.  在專案的 `ThisWorkbook` (Excel) 或 `ThisDocument` (Word) 類別 `ActionsPane` 欄位所包含的控制項中，加入自訂使用者控制項的執行個體。  
  
 如需示範此程序的更詳細的範例，請參閱[如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
## <a name="hiding-the-actions-pane"></a>隱藏執行窗格  
 雖然 <xref:Microsoft.Office.Tools.ActionsPane> 類別具有 <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> 方法和 <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> 屬性，但您不能使用 <xref:Microsoft.Office.Tools.ActionsPane> 類別本身的任何成員，從使用者介面移除執行窗格。 呼叫<xref:Microsoft.Office.Tools.ActionsPane.Hide%2A>方法或設定<xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>屬性**false**隱藏 [動作] 窗格中; 上的控制項不能隱藏工作窗格。  
  
 若要隱藏解決方案中的工作窗格，您有數個選項：  
  
-   對於 Word，設定<xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A>屬性<xref:Microsoft.Office.Interop.Word.TaskPane>物件，代表文件動作的工作窗格，以**false**。 下列程式碼範例宜從專案的 `ThisDocument` 類別執行。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  
  
-   對於 Excel，請設定<xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A>屬性<xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A>物件**false**。 下列程式碼範例宜從專案的 `ThisWorkbook` 類別執行。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  
  
-   Word 或 Excel，您可以另外設定<xref:Microsoft.Office.Core.CommandBar.Visible%2A>代表工作窗格之命令列屬性**false**。 下列程式碼範例宜從專案的 `ThisDocument` 或 `ThisWorkbook` 類別執行。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  
  
### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>在文件開啟時清除執行窗格  
 如果使用者在執行窗格仍顯示時儲存文件，則每次開啟文件時都會顯示執行窗格，不論執行窗格是否包含任何控制項。 如果想要控制其出現時機，請呼叫 `ThisDocument` 或 `ThisWorkbook` 的 `Startup` 事件處理常式中 `ActionsPane` 欄位的 <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> 方法，以確保文件開啟時不顯示執行窗格。  
  
### <a name="determining-when-the-actions-pane-is-closed"></a>判斷執行窗格關閉的時機  
 執行窗格關閉時未引發任何事件。 雖然 <xref:Microsoft.Office.Tools.ActionsPane> 類別具有 <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> 事件，但當使用者關閉執行窗格時並未引發這個事件。 藉由呼叫隱藏 [動作] 窗格中的控制項時，相反地，引發這個事件<xref:Microsoft.Office.Tools.ActionsPane.Hide%2A>方法或藉由設定<xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>屬性**false**。  
  
 如果終端使用者關閉了執行窗格，只要在應用程式的使用者介面 (UI) 中執行下列其中一個程序，就可以重新顯示。  
  
##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>使用 Word 或 Excel 的 UI 顯示執行窗格  
  
1.  在功能區中，按一下 [**檢視**] 索引標籤。  
  
2.  在**顯示/隱藏**群組中，按一下**文件動作**切換按鈕。  
  
## <a name="programming-actions-pane-events"></a>程式設計執行窗格事件  
 您可以將多個使用者控制項加入執行窗格，然後撰寫程式碼顯示和隱藏使用者控制項，來回應文件上的事件。 如果您將 XML 結構描述元素對應至文件，每當插入點位於其中一個 XML 元素內時，即可在執行窗格中顯示特定的使用者控制項。 如需詳細資訊，請參閱[如何： 對應至 Visual Studio 內的 Word 文件的結構描述](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)和[如何： 對應至 Visual Studio 內工作表的結構描述](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)。  
  
 您也可以撰寫程式碼來回應任何物件的事件，包括主控制項、應用程式或文件事件。 如需詳細資訊，請參閱[逐步解說： 程式設計針對事件 NamedRange 控制項的](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)。  
  
## <a name="binding-data-to-controls-on-the-actions-pane"></a>在執行窗格將資料繫結至控制項  
 執行窗格上的控制項和 Windows Form 上的控制項具有相同的資料繫結功能。 您可以將控制項繫結至資料來源，例如資料集、具類型資料集和 XML。 如需詳細資訊，請參閱 [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)。  
  
 您可以將執行窗格上的控制項和文件上的控制項繫結至相同的資料集。 例如，您可以在執行窗格的控制項和工作表的控制項之間，建立主要/詳細資料關聯。 如需詳細資訊，請參閱[逐步解說： 將資料繫結至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)。  
  
## <a name="validating-data-in-actions-pane-controls"></a>驗證執行窗格控制項中的資料  
 如果在動作窗格控制項的 <xref:System.Windows.Forms.Control.Validating> 事件處理常式中顯示訊息方塊，當焦點從控制項移到訊息方塊時，可能會再次引發該事件。 若要避免這個問題發生，請使用 <xref:System.Windows.Forms.ErrorProvider> 控制項顯示所有的驗證錯誤訊息。  
  
## <a name="user-control-stacking-order"></a>使用者控制項堆疊順序  
 如果您使用多個使用者控制項，無論執行窗格是垂直或水平停駐，您都可以撰寫程式碼，在執行窗格上適當堆疊使用者控制項。 您可以使用 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> 屬性的 <xref:Microsoft.Office.Tools.StackStyle> 列舉，設定執行窗格上的使用者控制項堆疊順序。 如需詳細資訊，請參閱[如何： 管理執行窗格上的控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> 屬性可以接受下列 <xref:Microsoft.Office.Tools.StackStyle> 列舉值。  
  
|堆疊樣式|定義|  
|--------------------|----------------|  
|FromBottom|從執行窗格底部堆疊。|  
|FromLeft|從執行窗格左邊堆疊。|  
|FromRight|從執行窗格右邊堆疊。|  
|FromTop|從執行窗格頂端堆疊。|  
|無|未定義堆疊順序，順序由開發人員控制。|  
  
 下列程式碼設定 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> 屬性從執行窗格頂端開始堆疊使用者控制項。  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  
  
## <a name="anchoring-controls"></a>錨定控制項  
 如果使用者在執行階段調整執行窗格的大小，控制項大小可隨著執行窗格調整。 您可以使用 Windows Form 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性，將控制項錨定到執行窗格。 您也可以相同方式將 Windows Form 控制項錨定到使用者控制項。 如需詳細資訊，請參閱[How to： 在 Windows Form 上控制項的錨定](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)。  
  
## <a name="resizing-the-actions-pane"></a>調整執行窗格大小  
 您不能直接變更 <xref:Microsoft.Office.Tools.ActionsPane> 的大小，因為 <xref:Microsoft.Office.Tools.ActionsPane> 內嵌在工作窗格中。 不過，您可設定代表工作窗格之 <xref:Microsoft.Office.Core.CommandBar> 的 <xref:Microsoft.Office.Core.CommandBar.Width%2A> 屬性，以程式設計方式變更工作窗格的寬度。 如果工作窗格以水平方式停駐或浮動，您可以變更其高度。  
  
 通常不建議以程式設計的方式調整工作窗格的大小，因為使用者應該要能夠選取最符合其需求的工作窗格大小。 不過，如果必須調整工作窗格的寬度，您可以使用下列程式碼完成這項工作。  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  
  
## <a name="repositioning-the-actions-pane"></a>重新置放執行窗格  
 您無法直接重新置放 <xref:Microsoft.Office.Tools.ActionsPane>，因為它內嵌在工作窗格中。 不過，您可設定代表工作窗格之 <xref:Microsoft.Office.Core.CommandBar> 的 <xref:Microsoft.Office.Core.CommandBar.Position%2A> 屬性，以程式設計方式移動工作窗格。  
  
 通常不建議以程式設計的方式重新置放工作窗格，因為使用者應該要能夠選擇最符合其需求的工作窗格位置。 不過，如果必須將工作窗格移至特定位置，您可以使用下列程式碼完成這項工作。  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  終端使用者可以隨時手動重新置放工作窗格。 沒有任何方式可以確保工作窗格會一直停駐在您以程式設計方式指定的位置上。 不過，您可以檢查方向的變更，確保執行窗格上的控制項依正確的方向堆疊。 如需詳細資訊，請參閱[如何： 管理執行窗格上的控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)。  
  
 設定 <xref:Microsoft.Office.Tools.ActionsPane> 的 <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> 和 <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> 屬性不會變更其位置，因為 <xref:Microsoft.Office.Tools.ActionsPane> 物件內嵌在工作窗格中。  
  
 如果工作窗格未停駐，您可以設定代表工作窗格之 <xref:Microsoft.Office.Core.CommandBar> 的 <xref:Microsoft.Office.Core.CommandBar.Top%2A> 和 <xref:Microsoft.Office.Core.CommandBar.Left%2A> 屬性。 下列程式碼會將未停駐的工作窗格移至文件的左上角。  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  
  
## <a name="see-also"></a>請參閱  
 [在 Office 方案中使用 WPF 控制項](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [逐步解說： 將文字插入文件中從 [動作] 窗格](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [逐步解說： 將資料繫結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [逐步解說： 將資料繫結至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [如何： 管理執行窗格控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [逐步解說：從執行窗格將文字插入文件](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  