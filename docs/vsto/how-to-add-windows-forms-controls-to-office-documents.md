---
title: HOW TO：將 Windows form 控制項加入 Office 文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 816f5b8d21578b57e93dab7349bfd877da11401c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869287"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>HOW TO：將 Windows Form 控制項加入 Office 文件
  您可以在文件層級專案的設計階段中，將 Windows Form 控制項加入 Microsoft Office Excel 和 Microsoft Office Word 文件。 在執行階段，您可以新增控制項，在文件層級自訂和 VSTO 增益集。例如，您可以將 <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> 控制項加入工作表，讓使用者可以從選項清單中進行選取。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 本主題說明下列工作：  
  
- [在設計階段加入控制項](#designtime)  
  
- [在文件層級專案中的執行階段加入控制項](#runtimedoclevel)  
  
- [在 VSTO 增益集的執行階段加入控制項](#runtimeaddin)  
  
  ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:您可以將控制項加入文件介面在執行階段？](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> 在設計階段加入控制項  
 您可以用幾種方式，透過文件層級專案，於設計階段將 Windows Form 控制項加入文件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>若要將 Windows Form 控制項拖曳至文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 **通用控制項**索引標籤**工具箱**、 按一下您要新增的控制項，並將它拖曳至文件。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>若要將 Windows Form 控制項拖曳至文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 **通用控制項**索引標籤**工具箱**，按一下您想要新增的控制項。  
  
3.  在文件上，在您希望成為控制項左上角的位置按一下，然後拖曳到希望成為控制項右下角的位置。  
  
     控制項會依指定的位置和大小加入文件。  
  
    > [!NOTE]  
    >  當您在 Excel 中選取控制項時，您會看到 **=EMBED("WinForms.Control.Host","")** 中**公式列**。 這個文字是必要的，不應該刪除。  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>若要按一下控制項，將 Windows Form 控制項加入文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 **通用控制項**索引標籤**工具箱**，按一下您想要新增的控制項  
  
3.  在文件中，按一下要加入控制項的位置。  
  
     控制項會依預設大小加入文件。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>若要按兩下控制項，將 Windows Form 控制項加入文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 **通用控制項**索引標籤**工具箱**，連按兩下您想要新增的控制項。  
  
     控制項會加入文件或現用窗格的中央位置。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>若要將 Windows Forms 控制項加入文件，藉由按下 Enter 鍵  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案資訊，請參閱[How to:在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在**通用控制項**索引標籤**工具箱**，按一下您想要新增，請按下的控制項**Enter**索引鍵。  
  
     控制項會加入文件或現用窗格的中央位置。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入控制項  
 您可以程式設計方式加入 Windows Form 控制項，在執行階段文件。 在 Word 中，請使用 `ThisDocument` 類別之 <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> 屬性的方法。 在 Excel 中，使用的方法<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A>的屬性`Sheet` *n*類別。 每個方法都有數個多載，可讓您以不同方式指定控制項的位置。  
  
 當您的 Windows Form 控制項加入文件在執行階段時，控制項不會保存在文件文件關閉時。 您可以在下一次開啟文件時重新建立該控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>若要在執行階段將 Windows Form 控制項  
  
1.  使用的方法有名稱加入\<*控制項類別*> (其中*控制類別*是您想要新增，例如在 Windows Form 控制項的類別名稱<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>)。  
  
     下列程式碼範例示範如何新增<xref:Microsoft.Office.Tools.Excel.Controls.Button>至儲存格**C5**的`Sheet1`適用於 Excel 的文件層級專案中。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集的執行階段加入控制項  
 您可以加入任何開啟的文件，在執行階段以程式設計方式加入 Windows Form 控制項。 首先，請依據開啟的文件或工作表，產生一個主項目。 然後，在 Word 中使用新主項目之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法。 在 Excel 中，則使用新主項目之 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 屬性的方法。 每個方法都有數個多載，可讓您以不同方式指定控制項的位置。  
  
 當您的 Windows Form 控制項加入文件在執行階段時，控制項不會保存在文件文件關閉時。 您可以在下一次開啟文件時重新建立該控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 如需在 VSTO 增益集專案中產生主項目的詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>若要在執行階段將 Windows Form 控制項  
  
1.  使用的方法有名稱加入\<*控制項類別*> (其中*控制類別*是您想要新增，例如在 Windows Form 控制項的類別名稱<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>)。  
  
    > [!NOTE]  
    >  在 VSTO 增益集中目標的專案中[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本中，您必須加入的參考*Microsoft.Office.Tools.Excel.v4.0.Utilities.dll*或*Microsoft.Office.Tools.Word.v4.0.Utilities.dll*組件才能存取 新增\<*控制項類別*> 方法。  
  
     下列程式碼範例示範如何使用 Word VSTO 增益集，將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 加入現用文件的第一個段落。  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>另請參閱  
 [在 Office 文件概觀上的 Windows Form 控制項](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：調整工作表儲存格內的控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
