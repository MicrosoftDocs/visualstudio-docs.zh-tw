---
title: HOW TO：將 Windows forms 控制項新增至 Office 檔
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
ms.openlocfilehash: a745794bb23902872f4b09c39eb8a3b3c1706137
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255875"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>作法：將 Windows Forms 控制項加入 Office 檔
  您可以在文件層級專案的設計階段中，將 Windows Form 控制項加入 Microsoft Office Excel 和 Microsoft Office Word 文件。 您可以在文件層級自訂和 VSTO 增益集的執行階段中，加入控制項。例如，您可以將 <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> 控制項加入工作表，讓使用者可以從選項清單中進行選取。

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 本主題說明下列工作：

- [在設計階段加入控制項](#designtime)

- [在檔層級專案中，于執行時間加入控制項](#runtimedoclevel)

- [在 VSTO 增益集的執行時間加入控制項](#runtimeaddin)

  ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範， [請參閱如何?：在執行時間將控制項加入檔介面？](http://go.microsoft.com/fwlink/?LinkId=132782).

## <a name="designtime"></a>在設計階段加入控制項
 您可以用幾種方式，透過文件層級專案，於設計階段將 Windows Form 控制項加入文件。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>若要將 Windows Form 控制項拖曳至文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的相關資訊[，請參閱如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您要加入的控制項，並將它拖曳至檔。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列] 看到 **=EMBED("WinForms.Control.Host","")** 。 這個文字是必要的，不應該刪除。

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>若要將 Windows Form 控制項拖曳至文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的相關資訊[，請參閱如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您想要加入的控制項。

3. 在文件上，在您希望成為控制項左上角的位置按一下，然後拖曳到希望成為控制項右下角的位置。

     控制項會依指定的位置和大小加入文件。

    > [!NOTE]
    > 當您在 Excel 中選取控制項時，您會在**公式**列中看到 **= EMBED （"WinForms"，""）** 。 這個文字是必要的，不應該刪除。

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>若要按一下控制項，將 Windows Form 控制項加入文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的相關資訊[，請參閱如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您想要加入的控制項

3. 在文件中，按一下要加入控制項的位置。

     控制項會依預設大小加入文件。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列] 看到 **=EMBED("WinForms.Control.Host","")** 。 這個文字是必要的，不應該刪除。

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>若要按兩下控制項，將 Windows Form 控制項加入文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的相關資訊[，請參閱如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按兩下您要加入的控制項。

     控制項會加入文件或現用窗格的中央位置。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列] 看到 **=EMBED("WinForms.Control.Host","")** 。 這個文字是必要的，不應該刪除。

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>若要按 Enter 鍵將 Windows Forms 控制項加入至檔

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的相關資訊[，請參閱如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您要加入的控制項，然後按下**enter**鍵。

     控制項會加入文件或現用窗格的中央位置。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列] 看到 **=EMBED("WinForms.Control.Host","")** 。 這個文字是必要的，不應該刪除。

## <a name="runtimedoclevel"></a>在檔層級專案中，于執行時間加入控制項
 您可以透過程式設計的方式，在執行階段將 Windows Form 控制項加入文件。 在 Word 中，請使用 `ThisDocument` 類別之 <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> 屬性的方法。 在 Excel 中，請使用<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> *n*類別之屬性`Sheet`的方法。 每個方法都有數個多載，可讓您以不同方式指定控制項的位置。

 當您在執行階段將 Windows Form 控制項加入文件時，若關閉文件，文件不會保存該控制項。 您可以在下一次開啟文件時重新建立該控制項。 如需詳細資訊，請參閱[在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

### <a name="to-add-a-windows-forms-control-at-run-time"></a>若要在執行階段加入 Windows Form 控制項

1. 使用具有\<name Add*控制項 class*> 的方法（其中*控制項類別*是您<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>想要加入之 Windows Forms 控制項的類別名稱，例如）。

     下列程式碼範例示範如何<xref:Microsoft.Office.Tools.Excel.Controls.Button> `Sheet1`在 Excel 的檔層級專案中，將加入儲存格**C5** 。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="runtimeaddin"></a>在 VSTO 增益集的執行時間加入控制項
 您可以透過程式設計的方式，在執行階段將 Windows Form 控制項加入任何開啟的文件。 首先，請依據開啟的文件或工作表，產生一個主項目。 然後，在 Word 中使用新主項目之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法。 在 Excel 中，則使用新主項目之 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 屬性的方法。 每個方法都有數個多載，可讓您以不同方式指定控制項的位置。

 當您在執行階段將 Windows Form 控制項加入文件時，若關閉文件，文件不會保存該控制項。 您可以在下一次開啟文件時重新建立該控制項。 如需詳細資訊，請參閱[在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

 如需在 VSTO 增益集專案中產生主專案的詳細資訊，請參閱[在 Vsto 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

### <a name="to-add-a-windows-forms-control-at-run-time"></a>若要在執行階段加入 Windows Form 控制項

1. 使用具有\<name Add*控制項 class*> 的方法（其中*控制項類別*是您<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>想要加入之 Windows Forms 控制項的類別名稱，例如）。

    > [!NOTE]
    > 在以或更新版本為目標的[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] VSTO 增益集專案中，您必須先加入對 Microsoft 的參考，然後才能存取 [新增]、[ *app-v 4.0* ] 或 [node.js] *.dll*元件。控制項類別 > 方法。 \<

     下列程式碼範例示範如何使用 Word VSTO 增益集，將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 加入現用文件的第一個段落。

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>另請參閱
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：調整工作表資料格內的控制項大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
