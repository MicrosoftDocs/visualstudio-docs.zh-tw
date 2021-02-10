---
title: 如何：將 Windows forms 控制項新增至 Office 檔
description: 瞭解如何在檔層級專案中，于設計階段將 Windows Forms 控制項加入 Microsoft Office Excel 和 Microsoft Office Word 檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d2f8d54e791acd7d027350caa3ce88c8eea9959
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954146"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>如何：將 Windows Forms 控制項新增至 Office 檔
  您可以在文件層級專案的設計階段中，將 Windows Form 控制項加入 Microsoft Office Excel 和 Microsoft Office Word 文件。 在執行時間，您可以在檔層級自訂和 VSTO 增益集中加入控制項。例如，您可以將控制項新增 <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> 至工作表，讓使用者可以從選項清單中選取。

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 本主題說明下列工作：

- [在設計階段加入控制項](#designtime)

- [在檔層級專案中的執行時間加入控制項](#runtimedoclevel)

- [在 VSTO 增益集的執行時間加入控制項](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> 在設計階段加入控制項
 您可以用幾種方式，透過文件層級專案，於設計階段將 Windows Form 控制項加入文件。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>若要將 Windows Form 控制項拖曳至文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您要加入的控制項，然後將它拖曳至檔。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>若要將 Windows Form 控制項拖曳至文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您要加入的控制項。

3. 在文件上，在您希望成為控制項左上角的位置按一下，然後拖曳到希望成為控制項右下角的位置。

     控制項會依指定的位置和大小加入文件。

    > [!NOTE]
    > 當您在 Excel 中選取控制項時，您會在 **公式** 列中看到 **= EMBED ( "WinForms"，"" )** 。 這個文字是必要的，不應該刪除。

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>若要按一下控制項，將 Windows Form 控制項加入文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您要新增的控制項

3. 在文件中，按一下要加入控制項的位置。

     控制項會依預設大小加入文件。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>若要按兩下控制項，將 Windows Form 控制項加入文件

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按兩下您要加入的控制項。

     控制項會加入文件或現用窗格的中央位置。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>按 Enter 鍵將 Windows Forms 控制項新增至檔

1. 在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。 如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 在 [**工具箱**] 的 [**通用控制項**] 索引標籤中，按一下您要新增的控制項，然後按下 **enter** 鍵。

     控制項會加入文件或現用窗格的中央位置。

    > [!NOTE]
    > 在 Excel 中選取控制項時，您會在 [資料編輯列]  看到 **=EMBED("WinForms.Control.Host","")**。 這個文字是必要的，不應該刪除。

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> 在檔層級專案中的執行時間加入控制項
 您可以透過程式設計的方式，在執行階段將 Windows Form 控制項加入文件。 在 Word 中，請使用 `ThisDocument` 類別之 <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> 屬性的方法。 在 Excel 中，使用 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> n 類別的屬性方法 `Sheet`  。 每個方法都有數個多載，可讓您以不同方式指定控制項的位置。

 當您在執行階段將 Windows Form 控制項加入文件時，若關閉文件，文件不會保存該控制項。 您可以在下一次開啟文件時重新建立該控制項。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

### <a name="to-add-a-windows-forms-control-at-run-time"></a>若要在執行階段加入 Windows Form 控制項

1. 使用名稱為 Add (的方法 \<*control class*> ，其中 *control 類別* 是您想要加入之 Windows Forms 控制項的類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>) 。

     下列程式碼範例示範如何 <xref:Microsoft.Office.Tools.Excel.Controls.Button>  `Sheet1` 在 Excel 的檔層級專案中，將加入儲存格 C5 的。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> 在 VSTO 增益集的執行時間加入控制項
 您可以透過程式設計的方式，在執行階段將 Windows Form 控制項加入任何開啟的文件。 首先，請依據開啟的文件或工作表，產生一個主項目。 然後，在 Word 中使用新主項目之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法。 在 Excel 中，則使用新主項目之 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 屬性的方法。 每個方法都有數個多載，可讓您以不同方式指定控制項的位置。

 當您在執行階段將 Windows Form 控制項加入文件時，若關閉文件，文件不會保存該控制項。 您可以在下一次開啟文件時重新建立該控制項。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

 如需在 VSTO 增益集專案中產生主專案的詳細資訊，請參閱 [在 Vsto 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

### <a name="to-add-a-windows-forms-control-at-run-time"></a>若要在執行階段加入 Windows Form 控制項

1. 使用名稱為 Add (的方法 \<*control class*> ，其中 *control 類別* 是您想要加入之 Windows Forms 控制項的類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>) 。

    > [!NOTE]
    > 在以或更新版本為目標的 VSTO 增益集專案中 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，您必須先加入 *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* 或 *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* 元件的參考，才能存取 Add \<*control class*> 方法。

     下列程式碼範例示範如何使用 Word VSTO 增益集，將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 加入現用文件的第一個段落。

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>另請參閱
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：調整工作表儲存格內的控制項大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
