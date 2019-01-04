---
title: HOW TO：以程式設計方式列印文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: da618b4b972c8f49d98118d26b5f0a4aa47cfde0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917351"
---
# <a name="how-to-programmatically-print-documents"></a>HOW TO：以程式設計方式列印文件
  您可以將整個 Microsoft Office Word 文件，或文件的一部分，列印到預設印表機。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>列印文件層級自訂一部分的文件  
  
### <a name="to-print-the-entire-document"></a>列印整份文件  
  
1.  在專案中呼叫 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 類別的 `ThisDocument` 方法來列印整份文件。 若要使用這個範例，請從 `ThisDocument` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
### <a name="to-print-the-current-page-of-the-document"></a>列印文件的目前頁面  
  
1.  在專案中呼叫 <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> 類別的 `ThisDocument` 方法，並指定要列印一份目前的頁面。 若要使用這個範例，請從 `ThisDocument` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="print-a-document-by-using-a-vsto-add-in"></a>使用 VSTO 增益集來列印文件  
  
### <a name="to-print-an-entire-document"></a>列印整份文件  
  
1.  呼叫您要列印之 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 方法。 下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
### <a name="to-print-the-current-page-of-a-document"></a>列印文件的目前頁面  
  
1.  呼叫您要列印之 <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 方法，並指定要列印一份目前的頁面。 下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
