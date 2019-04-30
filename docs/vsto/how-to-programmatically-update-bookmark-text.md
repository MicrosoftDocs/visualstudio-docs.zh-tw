---
title: HOW TO：以程式設計方式更新書籤文字
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 436fefd425da46cea6a8cd1aba95fb9eb14362f7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418967"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>HOW TO：以程式設計方式更新書籤文字
  您可以在 Microsoft Office Word 文件的預留位置書籤中插入文字，以便稍後擷取文字，或取代書籤中的文字。 如果開發的是文件層級自訂，您也可以更新繫結至資料的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項文字。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 書籤物件可以是下列兩種類型之一：

- <xref:Microsoft.Office.Tools.Word.Bookmark> 主控制項。

   <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項透過啟用資料繫結和公開事件，擴充原生 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件。 如需主控制項的詳細資訊，請參閱[主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。

- 原生 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件。

   <xref:Microsoft.Office.Interop.Word.Bookmark> 物件沒有事件或資料繫結功能。

  當您指派文字到書籤時，<xref:Microsoft.Office.Interop.Word.Bookmark> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 的行為不同。 如需詳細資訊，請參閱 <<c0> [ 書籤控制項](../vsto/bookmark-control.md)。

## <a name="use-host-controls"></a>使用主控制項

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>使用書籤控制項更新書籤內容

1. 建立採用 `bookmark` 引數作為書籤名稱，並採用 `newText` 引數作為要指派給 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性之字串的程序。

    > [!NOTE]
    > 指派文字給 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 或 <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> 屬性，將不會刪除書籤。

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. 指派*newText*字串<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>屬性<xref:Microsoft.Office.Tools.Word.Bookmark>。

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>使用 Word 物件

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>使用 Word 書籤物件更新書籤內容

1. 建立以 `bookmark` 引數作為 <xref:Microsoft.Office.Interop.Word.Bookmark> 的名稱，並以 `newText` 引數作為要指派給 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性之字串的程序。

    > [!NOTE]
    > 將文字指派給原生 Word <xref:Microsoft.Office.Interop.Word.Bookmark> 物件會刪除書籤。

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. 指派*newText*字串<xref:Microsoft.Office.Interop.Word.Range.Text%2A>屬性會自動刪除書籤的書籤。 然後重新將書籤加入 <xref:Microsoft.Office.Interop.Word.Bookmarks> 集合。

     下列程式碼範例可用於文件層級自訂。

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式將文字插入 Word 文件](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Word 物件模型概觀](../vsto/word-object-model-overview.md)
- [書籤控制項](../vsto/bookmark-control.md)
