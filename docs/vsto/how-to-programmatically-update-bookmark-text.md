---
title: 如何：以程式設計方式更新書簽文字
description: 瞭解如何使用 Visual Studio，以程式設計方式將文字插入 Microsoft Word 檔中的預留位置書簽。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826196"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>如何：以程式設計方式更新書簽文字
  您可以在 Microsoft Office Word 文件的預留位置書籤中插入文字，以便稍後擷取文字，或取代書籤中的文字。 如果開發的是文件層級自訂，您也可以更新繫結至資料的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項文字。 如需詳細資訊，請參閱 [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 書籤物件可以是下列兩種類型之一：

- <xref:Microsoft.Office.Tools.Word.Bookmark> 主控制項。

   <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項透過啟用資料繫結和公開事件，擴充原生 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件。 如需主控制項的詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

- 原生 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件。

   <xref:Microsoft.Office.Interop.Word.Bookmark> 物件沒有事件或資料繫結功能。

  當您指派文字到書籤時，<xref:Microsoft.Office.Interop.Word.Bookmark> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 的行為不同。 如需詳細資訊，請參閱 [書簽控制項](../vsto/bookmark-control.md)。

## <a name="use-host-controls"></a>使用主控制項

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>使用書籤控制項更新書籤內容

1. 建立採用 `bookmark` 引數作為書籤名稱，並採用 `newText` 引數作為要指派給 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性之字串的程序。

    > [!NOTE]
    > 指派文字給 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 或 <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> 屬性，將不會刪除書籤。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. 將 *newText* 字串指派給的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性 <xref:Microsoft.Office.Tools.Word.Bookmark> 。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>使用 Word 物件

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>使用 Word 書籤物件更新書籤內容

1. 建立以 `bookmark` 引數作為 <xref:Microsoft.Office.Interop.Word.Bookmark> 的名稱，並以 `newText` 引數作為要指派給 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性之字串的程序。

    > [!NOTE]
    > 將文字指派給原生 Word <xref:Microsoft.Office.Interop.Word.Bookmark> 物件會刪除書籤。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. 將 *newText* 字串指派給 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 書簽的屬性，它會自動刪除書簽。 然後重新將書籤加入 <xref:Microsoft.Office.Interop.Word.Bookmarks> 集合。

     下列程式碼範例可用於文件層級自訂。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在 Word 檔中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [書簽控制項](../vsto/bookmark-control.md)
