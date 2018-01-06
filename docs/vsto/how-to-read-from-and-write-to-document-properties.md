---
title: "如何： 讀取和寫入文件屬性 |Microsoft 文件"
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
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a484fdc9686e4454db801c2b6d503ae786b921f2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>如何：從文件屬性中讀取及寫入
  文件屬性可與文件一起儲存。 Office 應用程式提供許多內建屬性，例如作者、標題和主旨。 本主題說明如何設定 Microsoft Office Excel 和 Microsoft Office Word 的文件屬性。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何： 存取和 Microsoft Word 中操作自訂文件屬性？](http://go.microsoft.com/fwlink/?LinkId=136772)。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="setting-document-properties-in-excel"></a>設定 Excel 的文件屬性  
 若要處理 Excel 的內建屬性，請使用下列屬性:  
  
-   在文件層級專案中，使用 <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> 類別的 `ThisWorkbook` 屬性。  
  
-   在 VSTO 增益集專案中，則請使用 <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> 物件的 <xref:Microsoft.Office.Interop.Excel.Workbook> 屬性。  
  
 這些屬性會傳回 <xref:Microsoft.Office.Core.DocumentProperties> 物件，它是 <xref:Microsoft.Office.Core.DocumentProperty> 物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Item` 屬性擷取特定的屬性。  
  
 下列程式碼範例說明如何變更文件層級專案的內建 **Revision Number** 屬性。  
  
#### <a name="to-change-the-revision-number-property-in-excel"></a>變更 Excel 的修訂編號屬性  
  
1.  將內建的文件屬性指派給變數。  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  遞增 `Revision Number` 屬性，數目為一。  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="setting-document-properties-in-word"></a>設定 Word 的文件屬性  
 若要處理 Word 的內建屬性，請使用下列屬性:  
  
-   在文件層級專案中，使用 <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> 類別的 `ThisDocument` 屬性。  
  
-   在 VSTO 增益集專案中，則請使用 <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 屬性。  
  
 這些屬性會傳回 <xref:Microsoft.Office.Core.DocumentProperties> 物件，它是 <xref:Microsoft.Office.Core.DocumentProperty> 物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Item` 屬性擷取特定的屬性。  
  
 下列程式碼範例說明如何變更文件層級專案的內建 **Subject** 屬性。  
  
#### <a name="to-change-the-subject-property"></a>變更主旨屬性  
  
1.  將內建的文件屬性指派給變數。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  將 `Subject` 屬性變更成「白皮書」。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 此範例假設，在 Excel 文件層級專案的 `ThisWorkbook` 類別和 Word 文件層級專案的 `ThisDocument` 類別中，您已經撰寫了程式碼。  
  
 雖然您處理的是 Word 和 Excel 及其物件，但 Microsoft Office 仍會提供可用的內建文件屬性清單。 嘗試存取未定義的屬性會引發例外狀況。  
  
## <a name="see-also"></a>請參閱  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [如何：建立及修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  