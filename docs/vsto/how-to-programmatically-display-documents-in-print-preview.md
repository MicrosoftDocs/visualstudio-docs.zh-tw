---
title: 如何：以程式設計方式在預覽列印中顯示檔
description: 瞭解如何在 Microsoft Word 檔中，以程式設計方式在預覽列印中顯示檔。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90979fbc7cd0b46329b8d9e9bc142e8cf0066db0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825884"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>如何：以程式設計方式在預覽列印中顯示檔
  如果您的方案會產生報告，您可能想要在 [預覽列印] 模式中向使用者顯示報告。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>檔層級自訂的程式

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>呼叫 PrintPreview 方法以在預覽列印中顯示文件

1. 請呼叫 <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> 類別的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>設定 PrintPreview 屬性以在預覽列印中顯示文件

1. 將 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Application> 屬性設定為 **true**。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>VSTO 增益集的程序

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>呼叫 PrintPreview 方法以在預覽列印中顯示文件

1. 呼叫您要預覽之 <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> 的 <xref:Microsoft.Office.Interop.Word.Document> 方法。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>設定 PrintPreview 屬性以在預覽列印中顯示文件

1. 將 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Application> 屬性設定為 **true**。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式列印檔案](../vsto/how-to-programmatically-print-documents.md)
- [如何：以程式設計方式開啟現有檔](../vsto/how-to-programmatically-open-existing-documents.md)
- [如何：以程式設計方式建立新檔](../vsto/how-to-programmatically-create-new-documents.md)
