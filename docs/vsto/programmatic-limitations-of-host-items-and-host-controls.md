---
title: 主專案和主控制項的程式設計限制
description: 瞭解主專案和主控制項的行為，以及在執行時間的原生 Office 物件之間的基本差異。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 08205473636a04dbc742b6c09c99e9771094f61c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525129"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>主專案和主控制項的程式設計限制
  每個主項目和主控制項的行為，都已設計成像是對應的原生 Microsoft Office Word 或 Microsoft Office Excel 物件一樣，同時還具備額外的功能。 不過，主項目和主控制項在執行階段的行為，還是與原生 Office 物件有些基本差異。

 如需主專案和主控制項的一般資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>以程式設計方式建立主專案
 當您在執行階段使用 Word 或 Excel 物件模型，以程式設計方式建立或開啟文件、活頁簿或工作表時，此項目並不是主項目。 相反地，這個新物件是原生 Office 物件。 例如，如果您在執行階段使用 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法建立新的 Word 文件，該文件會是原生 <xref:Microsoft.Office.Interop.Word.Document> 物件，而不是 <xref:Microsoft.Office.Tools.Word.Document> 主項目。 同樣地，當您在執行階段使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 方法建立新工作表時，您會得到原生 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，而不是 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。

 在文件層級專案中，您無法在執行階段建立主項目。 主項目只能在文件層級專案的設計階段建立。 如需詳細資訊，請參閱 [檔主專案](../vsto/document-host-item.md)、活頁 [簿主專案](../vsto/workbook-host-item.md)和 [工作表主專案](../vsto/worksheet-host-item.md)。

 在 VSTO 增益集專案中，您可以在執行階段建立 <xref:Microsoft.Office.Tools.Word.Document>、 <xref:Microsoft.Office.Tools.Excel.Workbook>或 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="programmatically-create-host-controls"></a>以程式設計方式建立主控制項
 您可以在執行階段，以程式設計方式將主控制項加入 <xref:Microsoft.Office.Tools.Word.Document> 或 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

 您無法將主控制項加入原生 <xref:Microsoft.Office.Interop.Word.Document> 或 <xref:Microsoft.Office.Interop.Excel.Worksheet>。

> [!NOTE]
> 下列主控制項無法以程式設計方式加入工作表或文件： <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>和 <xref:Microsoft.Office.Tools.Word.XMLNodes>。

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>瞭解主專案、主控制項和原生 Office 物件之間的類型差異
 在每個主項目和主控制項中，都有基礎的原生 Microsoft Office Word 或 Microsoft Office Excel 物件。 您可以使用主專案或主控制項的 InnerObject 屬性來存取基礎物件。 不過，您無法將原生 Office 物件轉換成其對應的主項目或主控制項。 如果您嘗試將原生 Office 物件轉換成主項目或主控制項的類型，將會擲回 <xref:System.InvalidCastException> 。

 在幾種情況下，主項目和主控制項與基礎原生 Office 物件之間的類型差異，可能會影響您的程式碼。

### <a name="pass-host-controls-to-methods-and-properties"></a>將主控制項傳遞至方法和屬性
 在 Word 中，您無法將主控制項傳遞至需要原生 Word 物件做為參數的方法或屬性。 您必須使用主控制項的 InnerObject 屬性來傳回基礎原生單字物件。 例如，您可以藉由將 <xref:Microsoft.Office.Interop.Word.Bookmark> 主控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> 屬性傳遞至方法，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 物件傳遞至方法。

 在 Excel 中，當方法或屬性預期基礎 Excel 物件時，您必須使用主控制項的 InnerObject 屬性，將主控制項傳遞至方法或屬性。

 下列範例會建立 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，並將其傳遞至 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法。 這個程式碼使用具名範圍的 <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> 屬性，傳回 <xref:Microsoft.Office.Interop.Excel.Range> 方法所需的基礎 Office <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 。

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>原生 Office 方法和屬性的傳回類型
 主項目的大多數方法和屬性都會傳回主項目所依據的基礎原生 Office 物件。 例如，Excel 之 <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> 主控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 屬性會傳回 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，而不是 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 同樣地，Word 之 <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> 主控制項的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 屬性會傳回 <xref:Microsoft.Office.Interop.Word.Document> 物件，而不是 <xref:Microsoft.Office.Tools.Word.Document> 主項目。

### <a name="access-collections-of-host-controls"></a>存取主控制項的集合
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 不會為每種主控制項類型提供個別集合。 相反地，請使用主專案的 Controls 屬性來逐一查看所有 managed 控制項， (主控制項和檔或工作表上) 的 Windows Forms 控制項，然後尋找符合您感興趣之主控制項類型的專案。 下列程式碼範例會檢查 Word 文件上的每個控制項，並判斷控制項是否為 <xref:Microsoft.Office.Tools.Word.Bookmark>。

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 如需主專案之控制項屬性的詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

 Word 和 Excel 物件模型包含在文件和工作表上公開原生控制項集合的屬性。 您無法使用這些屬性來存取 Managed 控制項。 例如，您無法使用 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> 屬性或 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> 屬性，來列舉文件中的每個 <xref:Microsoft.Office.Tools.Word.Document>主控制項。 這些屬性只會包含文件中的 <xref:Microsoft.Office.Interop.Word.Bookmark> 控制項，而不會包含文件中的 <xref:Microsoft.Office.Tools.Word.Bookmark> 主控制項。

## <a name="see-also"></a>另請參閱
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [工作表主專案](../vsto/worksheet-host-item.md)
- [活頁簿主專案](../vsto/workbook-host-item.md)
- [檔主專案](../vsto/document-host-item.md)
