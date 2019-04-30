---
title: HOW TO：以程式設計方式在預覽列印中顯示文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8296d28e884c746e09b427914af02213bbbaa7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813032"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>HOW TO：以程式設計方式在預覽列印中顯示文件
  如果您的方案會產生報告，您可能想要在 [預覽列印] 模式中向使用者顯示報告。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>文件層級自訂中的程序

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>呼叫 PrintPreview 方法以在預覽列印中顯示文件

1. 請呼叫 <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> 類別的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>設定 PrintPreview 屬性以在預覽列印中顯示文件

1. 將 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Application> 屬性設定為 **true**。

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>VSTO 增益集的程序

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>呼叫 PrintPreview 方法以在預覽列印中顯示文件

1. 呼叫您要預覽之 <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> 的 <xref:Microsoft.Office.Interop.Word.Document> 方法。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>設定 PrintPreview 屬性以在預覽列印中顯示文件

1. 將 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Application> 屬性設定為 **true**。

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式列印文件](../vsto/how-to-programmatically-print-documents.md)
- [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)
- [如何：以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)
