---
title: 如何：以程式設計方式在檔中加入頁首和頁尾
description: 瞭解如何使用區段的標頭屬性和頁尾屬性，將文字新增至檔中的頁首和頁尾。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1abf9c0726a6b4afd1764aec095f129a4fcaf510
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844513"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>如何：以程式設計方式在檔中加入頁首和頁尾
  您可以使用 <xref:Microsoft.Office.Interop.Word.Section> 的 <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> 屬性和 <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> 屬性，將文字加入文件的頁首和頁尾。 文件的每個區段都包含三個頁首和頁尾：

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  文件層級自訂與 VSTO 增益集的程序不同。

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>文件層級自訂
 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行範例。

### <a name="to-add-text-to-footers-in-the-document"></a>將文字加入文件的頁尾

1. 下列程式碼範例會設定文件每個區段的主要頁尾要插入的文字字型，然後將文字插入頁尾。

     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>將文字加入文件的頁首

1. 下列程式碼範例會在文件的每個頁首加入顯示頁碼的欄位，然後設定段落對齊方式，讓文字向頁首的右邊靠齊。

     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]

## <a name="vsto-add-ins"></a>VSTO 增益集
 若要使用下列程式碼範例，請從專案的 `ThisAddIn` 類別中執行範例。

### <a name="to-add-text-to-footers-in-a-document"></a>將文字加入文件的頁尾

1. 下列程式碼範例會設定文件每個區段的主要頁尾要插入的文字字型，然後將文字插入頁尾。 這個程式碼範例使用使用中文件。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>將文字加入文件的頁首

1. 下列程式碼範例會在文件的每個頁首加入顯示頁碼的欄位，然後設定段落對齊方式，讓文字向頁首的右邊靠齊。 這個程式碼範例使用使用中文件。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立新檔](../vsto/how-to-programmatically-create-new-documents.md)
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [如何：以程式設計方式在檔中找到的專案之間執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
