---
title: "在執行階段將控制項加入 Office 文件 |Microsoft 文件"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
ms.assetid: 4f43b3eb-f0ec-44e2-9885-6ede327c6913
caps.latest.revision: "102"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d29fd74ee92344ac8b2eedbe4a5b8838171d7d96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="adding-controls-to-office-documents-at-run-time"></a>在執行階段將控制項加入至 Office 文件
  您可以在執行階段將控制項加入 Microsoft Office Word 文件與 Microsoft Office Excel 活頁簿中。 您也可以在執行階段加以移除。 您在執行階段加入或移除的控制項稱為 *動態控制項*。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 本主題說明下列項目：  
  
-   [在執行階段使用控制項集合來管理控制項](#ControlsCollection)。  
  
-   [將主控制項加入文件中](#HostControls)。  
  
-   [將 Windows Form 控制項加入文件中](#WindowsForms)。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何： 將控制項加入在執行階段文件介面？](http://go.microsoft.com/fwlink/?LinkId=132782)。  
  
##  <a name="ControlsCollection"></a> Managing Controls at Run Time by Using the Control Collections  
 若要在執行階段加入、取得或移除控制項，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 與 <xref:Microsoft.Office.Tools.Word.ControlCollection> 物件的 Helper 方法。  
  
 您存取這些物件的方式，取決於您所開發的專案類型：  
  
-   在 Excel 的文件層級專案中，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 、 `Sheet1`與 `Sheet2`類別的 `Sheet3` 屬性。 如需有關這些類別的詳細資訊，請參閱[工作表主項目](../vsto/worksheet-host-item.md)。  
  
-   在 Word 的文件層級專案中，請使用 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 類別的 `ThisDocument` 屬性。 如需此類別的詳細資訊，請參閱[文件主項目](../vsto/document-host-item.md)。  
  
-   在 VSTO 增益集專案中的 Excel 或 Word，使用的控制項屬性<xref:Microsoft.Office.Tools.Excel.Worksheet>或<xref:Microsoft.Office.Tools.Word.Document>您在執行階段所產生。 如需有關如何在執行階段產生這些物件的詳細資訊，請參閱[擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### <a name="adding-controls"></a>加入控制項  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 與 <xref:Microsoft.Office.Tools.Word.ControlCollection> 類型包括 Helper 方法，其可用來將主控制項和通用 Windows Form 控制項加入文件與工作表中。 每個方法名稱皆具有格式 `Add`*控制項類別*，其中 *控制項類別* 是您想要加入的控制項類別名稱。 例如，若要將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入文件中，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> 方法。  
  
 下列程式碼範例在 Excel 的文件層級專案中，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 加入 `Sheet1` 中。  
  
 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  
  
### <a name="accessing-and-deleting-controls"></a>存取與刪除控制項  
 您可以使用的控制項屬性<xref:Microsoft.Office.Tools.Excel.Worksheet>或<xref:Microsoft.Office.Tools.Word.Document>來逐一查看文件，包括您在設計階段加入控制項中的所有控制項。 您在設計階段加入的控制項也稱為 *靜態控制項*。  
  
 您可以移除動態控制項，藉由呼叫 Delete 方法的控制項，或藉由呼叫每個控制項集合的 Remove 方法。 下列程式碼範例在 Excel 的文件層級專案中使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> 方法，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 從 `Sheet1` 移除。  
  
 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  
  
 您無法在執行階段移除靜態控制項。 如果您嘗試移除靜態控制項，請使用刪除或移除方法<xref:Microsoft.Office.Tools.CannotRemoveControlException>就會擲回。  
  
> [!NOTE]  
>  在文件的 `Shutdown` 事件處理常式中，請勿以程式設計方式移除控制項。 當 `Shutdown` 事件受到引發時，文件的 UI 項目便無法再使用。 如果您想在文件關閉前移除控制項，請將程式碼加入另一個事件的事件處理常式中，例如 <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> 或 <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> (針對 Word)，或是 <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>或 <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> (針對 Excel)。  
  
##  <a name="HostControls"></a> Adding Host Controls to Documents  
 在您以程式設計方式將主控制項加入文件中時，您必須提供控制項的唯一識別名稱，且必須指定要將控制項加入文件的所在位置。 如需特定的相關指示，請參閱下列主題：  
  
-   [如何：將 ListObject 控制項新增至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [如何：將 NamedRange 控制項新增至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [如何：將圖表控制項新增至工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [如何：將內容控制項新增至 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [如何：將書籤控制項新增至 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
 如需主控制項的詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 在文件儲存後關閉時，所有動態建立的主控制項皆會與其事件中斷連接，並失去其資料繫結功能。 您可以將程式碼加入方案中，以便在文件重新開啟時重新建立主控制項。 如需詳細資訊，請參閱 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
> [!NOTE]  
>  未替下列主控制項提供 Helper 方法，原因是這些控制項不能以程式設計方式加入文件中： <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>與 <xref:Microsoft.Office.Tools.Word.XMLNodes>。  
  
##  <a name="WindowsForms"></a> Adding Windows Forms Controls to Documents  
 在您以程式設計方式將 Windows Form 控制項加入文件中時，您必須提供控制項位置，以及控制項的唯一識別名稱。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 為每個控制項提供 Helper 方法。 這些方法受到多載，以便讓您為控制項的位置傳遞一定範圍或特定的座標。  
  
 在文件儲存後關閉時，所有動態建立的 Windows Form 控制項會從文件中移除。 您可以將程式碼加入方案中，以便在文件重新開啟時重新建立控制項。 如果您使用 VSTO 增益集來建立動態的 Windows Form 控制項，則控制項的 ActiveX 包裝函式會保留在文件中。 如需詳細資訊，請參閱 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
> [!NOTE]  
>  Windows Form 控制項無法以程式設計方式加入受保護的文件中。 如果您以程式設計方式將 Word 文件或 Excel 工作表取消保護以加入控制項，則您必須撰寫額外的程式碼，以便在文件關閉時移除控制項的 ActiveX 包裝函式。 控制項的 ActiveX 包裝函式不會自動從受保護的文件刪除。  
  
### <a name="adding-custom-controls"></a>加入自訂控制項  
 如果您想要加入 <xref:System.Windows.Forms.Control> ，而其不受可用的 Helper 方法支援 (例如自訂使用者控制項)，請使用下列方法：  
  
-   針對 Excel，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> 物件的其中一種 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 方法 。  
  
-   針對 Word，請使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> 物件的其中一種 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 。  
  
 若要加入該控制項，將傳遞<xref:System.Windows.Forms.Control>、 的位置控制項，以及可唯一識別控制項 AddControl 方法名稱。 AddControl 方法會傳回物件，用於定義控制項如何互動的工作表或文件。 AddControl 方法會傳回<xref:Microsoft.Office.Tools.Excel.ControlSite>（針對 Excel) 或<xref:Microsoft.Office.Tools.Word.ControlSite>（適用於 Word) 的物件。  
  
 下列程式碼範例示範如何使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> 方法，以動態方式將自訂使用者控制項加入文件層級 Excel 專案的工作表中。 在此範例中，使用者控制項名為 `UserControl1`，而 <xref:Microsoft.Office.Interop.Excel.Range> 名為 `range1`。 若要使用此範例，請從專案中的 `Sheet`*n* 類別加以執行。  
  
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  
  
### <a name="using-members-of-custom-controls"></a>使用自訂控制項的成員  
 使用其中一種 AddControl 方法來將控制項加入工作表或文件之後, 您現在有兩個不同的控制項物件：  
  
-   <xref:System.Windows.Forms.Control> 代表自訂控制項。  
  
-   ControlSite、 OLEObject 或 OLEControl 物件後，表示控制項已將它加入工作表或文件。  
  
 這些控制項之間共用許多屬性和方法。 請務必透過適當的控制項存取這些成員：  
  
-   若要存取僅屬於自訂控制項的成員，請使用 <xref:System.Windows.Forms.Control>。  
  
-   若要存取控制項所共用的成員，請使用 ControlSite、 OLEObject 或 OLEControl 物件。  
  
 如果您從 <xref:System.Windows.Forms.Control>存取共用的成員，其可能會在沒有警告或通知的情況下失敗，或產生無效的結果。 一律使用 ControlSite、 OLEObject 或 OLEControl 物件的方法或屬性，除非方法或所需的屬性不是可使用;您要則只應參考<xref:System.Windows.Forms.Control>。  
  
 如需範例，<xref:Microsoft.Office.Tools.Excel.ControlSite>類別和<xref:System.Windows.Forms.Control>類別有 Top 的屬性。 若要取得或設定控制項的頂端和文件頂端之間的距離，請使用 <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> 的 <xref:Microsoft.Office.Tools.Excel.ControlSite>屬性，而非 <xref:System.Windows.Forms.Control.Top%2A> 的 <xref:System.Windows.Forms.Control>屬性。  
  
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  
  
## <a name="see-also"></a>請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [如何： 將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何： 將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [如何： 將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [如何： 將內容控制項加入 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何：將 Windows Forms 控制項新增至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
