---
title: 如何：調整書簽控制項的大小
description: 瞭解當您將書簽控制項新增至 Microsoft Word 檔時，如何使用 Visual Studio 設定書簽控制項的大小。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b2b2bd963b2f0b4eb574630382930eb0805909be
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825780"
---
# <a name="how-to-resize-bookmark-controls"></a>如何：調整書簽控制項的大小
  您可以在將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入 Microsoft Office Word 文件時，設定控制項的大小； 也可以稍後再調整大小。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 調整書籤大小的方法有三種：

- 在 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項中加入或移除文字。

   每當您在書籤中加入文字時，都會自動放大書籤，以包含新的文字。 當您刪除文字時，則會自動縮小書籤。

- 變更 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 屬性。

   如果變更的大小只有幾個字元，則適合這種方法。

- 重新建立 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。

   如果要大幅變更書籤的大小或位置，則適合這種方法。

  在文件層級的專案中，您可以於設計階段或執行階段，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入專案中的文件。 在 VSTO 增益集專案中，您可以於執行階段將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入任何開啟的文件。 如需詳細資訊，請參閱 [如何：將書簽控制項新增至 Word 檔](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>變更開始和結束屬性

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>在文件層級專案中，於設計階段調整書籤大小

1. 選取 [屬性]  視窗中的書籤。

2. 增加或減少 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 屬性的值。

3. 增加或減少 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 屬性的值。

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>在文件層級專案中，於執行階段調整書籤大小

1. 修改您在執行階段或設計階段建立之 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 屬性。

     下列程式碼範例會將五個字元加入名為 `SampleBookmark`的書籤開頭。 這段程式碼假設書籤之前的文字至少有五個字元。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet2":::

     下列程式碼範例會將五個字元加入同一個書籤的結尾。 這段程式碼假設書籤之後的文字至少有五個字元。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet3":::

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-run-time"></a>在 VSTO 增益集專案中，于執行時間調整書簽大小

1. 修改您在執行階段建立之 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 屬性。

     下列程式碼範例會建立在使用中文件第一個段落中包含文字的 <xref:Microsoft.Office.Tools.Word.Bookmark> ，然後再從 <xref:Microsoft.Office.Tools.Word.Bookmark>的開頭和結尾移除五個字元。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet16":::

## <a name="recreate-the-bookmark"></a>重新建立書簽
 您可以透過加入與現有書籤同名但大小不同的新書籤，來調整文件層級專案中的書籤大小。

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>在文件層級專案中，於設計階段重新建立書籤

1. 選取要包含在新 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項的文字。

2. 按一下 [插入]  功能表上的 [書籤] 。

3. 在 [書籤]  對話方塊中，輸入您要調整大小的書籤名稱，然後按一下 [加入] 。

## <a name="see-also"></a>另請參閱
- [如何：將書簽控制項新增至 Word 檔](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)
- [如何：調整 ListObject 控制項的大小](../vsto/how-to-resize-listobject-controls.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
