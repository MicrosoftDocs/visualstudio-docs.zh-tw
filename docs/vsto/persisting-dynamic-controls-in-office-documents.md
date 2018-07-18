---
title: 保存動態控制項中的 Office 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b77310f797db3eb031bc311f4fc68bc7fd6b4c56
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059242"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>保存動態控制項中的 Office 文件

文件或活頁簿儲存和關閉時，不會保存在執行階段加入的控制項。 主控制項和 Windows Form 控制項的確切行為不相同。 在這兩種情況下，您都可以將程式碼加入方案中，以便在使用者重新開啟文件時，重新建立控制項。

您在執行階段加入文件的控制項稱為 *動態控制項*。 如需有關動態控制項的詳細資訊，請參閱[將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>保存在文件中的主控制項

在文件儲存後關閉時，所有動態主控制項都會從文件中移除。 只有基礎原生 Office 物件會保留下來。 例如，<xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName>主控制項會變為<xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>。 原生 Office 物件未連接到主控制項事件，且不具有主控制項的資料繫結功能。

下表為各類主控制項列出文件中所遺留的原生 Office 物件。

|主控制項類型|原生 Office 物件類型|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>文件開啟時，重新建立動態主控制項

每當使用者開啟文件時，您都可以重新建立動態主控制項來取代現有的原生控制項。 在文件開啟時以這種方式建立主控制項，便會模擬使用者可能預期的經驗。

若要重新建立 Word，主控制項或<xref:Microsoft.Office.Tools.Excel.NamedRange>或<xref:Microsoft.Office.Tools.Excel.ListObject>for Excel，使用主控制項`Add` \<*控制項類別*> 方法<xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName>或<xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName>物件。 使用具有原生 Office 物件參數的方法。

例如，如果您想要建立<xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName>主控制項從現有的原生<xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>文件開啟時，使用<xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A>方法並傳入現有<xref:Microsoft.Office.Interop.Excel.ListObject>。 下列程式碼範例示範如何在 Excel 的文件層級專案中執行這項作業。 此程式碼重新建立動態 <xref:Microsoft.Office.Tools.Excel.ListObject> ，其以 <xref:Microsoft.Office.Interop.Excel.ListObject> 類別中名為 `MyListObject` 的現有 `Sheet1` 為基礎。

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>重新建立圖表

若要重新建立<xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>主控制項，您必須先刪除原生<xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>，然後再重新建立<xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>使用<xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>方法。 沒有任何`Add` \<*控制項類別*> 方法可讓您建立新<xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>根據現有<xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>。

如果您未先刪除原生<xref:Microsoft.Office.Interop.Excel.Chart>，然後重新建立時，您將建立第二個且重複的圖表<xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>。

## <a name="persist-windows-forms-controls-in-documents"></a>保存在文件中的 Windows Form 控制項

在文件儲存後關閉時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會自動將所有動態建立的 Windows Form 控制項從文件中移除。 不過，文件層級與 VSTO 增益集專案的行為不相同。

在文件層級的自訂中，控制項及其基礎 ActiveX 包裝函式 (用以主控文件上的控制項) 會在下一次文件開啟時遭到移除。 沒有任何跡象指出控制項曾存在其中。

在 VSTO 增益集中，控制項會遭到移除，但 ActiveX 包裝函式會保留在文件中。 下一次使用者開啟文件時，便可看見 ActiveX 包裝函式。 在 Excel 中，ActiveX 包裝函式會顯示控制項的影像，與文件最近一次儲存時所顯示的相同。 在 Word 中，使用者需加以點選才能看見 ActiveX 包裝函式，在此情況下會顯示一條虛線表示控制項的框線。 有幾種方法可以移除 ActiveX 包裝函式。 如需詳細資訊，請參閱 <<c0> [ 移除 ActiveX 包裝函式中的增益集](#removingActiveX)。

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>文件開啟時，重新建立 Windows Form 控制項

您可以在使用者重新開啟文件時，重新建立已刪除的 Windows Form 控制項。 若要這樣做，您的解決方案必須執行下列工作：

1.  在文件儲存或關閉時，儲存控制項的相關資訊，包括其大小、位置與狀態。 文件層級自訂中，您可以將資料儲存到文件中的資料快取。 在 VSTO 增益集中，您可以將資料儲存到文件中的自訂 XML 組件。

2.  重新建立文件開啟時所引發事件的控制項。 在文件層級專案中，您可以在 `Sheet`*n*`_Startup` 或 `ThisDocument_Startup` 事件處理常式中執行此作業。 在 VSTO 增益集專案中，您可以在 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 或 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的處理常式中執行此作業。

###  <a name="removingActiveX"></a> 移除增益集中的 ActiveX 包裝函式

當您將動態 Windows Form 控制項加入文件使用 VSTO 增益集時，您可以防止控制項的 ActiveX 包裝函式不會出現在文件以下列方式開啟下一次。

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>文件開啟時移除 ActiveX 包裝函式

若要移除所有的 ActiveX 包裝函式，呼叫`GetVstoObject`方法來產生的主項目<xref:Microsoft.Office.Interop.Word.Document>或<xref:Microsoft.Office.Interop.Excel.Workbook>表示新開啟的文件。 例如，若要移除的 Word 文件中的所有 ActiveX 包裝函式，您可以呼叫`GetVstoObject`方法來產生的主項目<xref:Microsoft.Office.Interop.Word.Document>物件傳遞至事件處理常式，如<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>事件。

若文件僅會在安裝 VSTO 增益集的電腦上開啟，則此程序會很有用。 如果文件可能會傳遞至未安裝 VSTO 增益集的其他使用者，請考慮改為在關閉文件前移除控制項。

下列程式碼範例示範如何呼叫`GetVstoObject`文件開啟時的方法。

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

雖然`GetVstoObject`方法主要用來產生新的主項目，在執行階段，這個方法也會清除文件中的所有 ActiveX 包裝函式呼叫為特定的文件的第一次。 如需有關如何使用`GetVstoObject`方法，請參閱 <<c2> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

如果您 VSTO 增益集建立動態控制項，開啟文件時，您 VSTO 增益集將會已呼叫`GetVstoObject`方法建立控制項的程序的一部分。 您不需要新增個別呼叫`GetVstoObject`方法，在此案例中移除 ActiveX 包裝函式。

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>文件關閉前移除動態控制項

您的 VSTO 增益集可以在文件關閉前，明確地從文件移除每個動態控制項。 若文件可能會傳遞至未安裝 VSTO 增益集的其他使用者，則此程序會很有用。

下列程式碼範例示範如何在 Word 文件關閉時，從該文件移除所有的 Windows Form 控制項。

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>另請參閱

- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
