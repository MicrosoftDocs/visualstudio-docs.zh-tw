---
title: HOW TO：讀取和寫入文件屬性
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac0d81c9e42a5c3aa22a09d59f346e6127b1284f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115766"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>HOW TO：讀取和寫入文件屬性
  文件屬性可與文件一起儲存。 Office 應用程式提供許多內建屬性，例如作者、標題和主旨。 本主題說明如何設定 Microsoft Office Excel 和 Microsoft Office Word 的文件屬性。

 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:存取和操作 Microsoft Word 中的自訂文件屬性？](http://go.microsoft.com/fwlink/?LinkId=136772).

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>在 Excel 中的設定文件屬性
 若要處理 Excel 的內建屬性，請使用下列屬性:

- 在文件層級專案中，使用 <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> 類別的 `ThisWorkbook` 屬性。

- 在 VSTO 增益集專案中，則請使用 <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> 物件的 <xref:Microsoft.Office.Interop.Excel.Workbook> 屬性。

  這些屬性會傳回 <xref:Microsoft.Office.Core.DocumentProperties> 物件，它是 <xref:Microsoft.Office.Core.DocumentProperty> 物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Item` 屬性擷取特定的屬性。

  下列程式碼範例說明如何變更文件層級專案的內建 **Revision Number** 屬性。

### <a name="to-change-the-revision-number-property-in-excel"></a>變更 Excel 的修訂編號屬性

1. 將內建的文件屬性指派給變數。

     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]

2. 遞增 `Revision Number` 屬性，數目為一。

     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]

## <a name="set-document-properties-in-word"></a>在 Word 中的設定文件屬性
 若要處理 Word 的內建屬性，請使用下列屬性:

- 在文件層級專案中，使用 <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> 類別的 `ThisDocument` 屬性。

- 在 VSTO 增益集專案中，則請使用 <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 屬性。

  這些屬性會傳回 <xref:Microsoft.Office.Core.DocumentProperties> 物件，它是 <xref:Microsoft.Office.Core.DocumentProperty> 物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Item` 屬性擷取特定的屬性。

  下列程式碼範例說明如何變更文件層級專案的內建 **Subject** 屬性。

### <a name="to-change-the-subject-property"></a>變更主旨屬性

1. 將內建的文件屬性指派給變數。

     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]

2. 將 `Subject` 屬性變更成「白皮書」。

     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]

## <a name="robust-programming"></a>穩固程式設計
 此範例假設，在 Excel 文件層級專案的 `ThisWorkbook` 類別和 Word 文件層級專案的 `ThisDocument` 類別中，您已經撰寫了程式碼。

 雖然您處理的是 Word 和 Excel 及其物件，但 Microsoft Office 仍會提供可用的內建文件屬性清單。 嘗試存取未定義的屬性會引發例外狀況。

## <a name="see-also"></a>另請參閱
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [程式文件層級自訂](../vsto/programming-document-level-customizations.md)
- [如何：建立和修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)
