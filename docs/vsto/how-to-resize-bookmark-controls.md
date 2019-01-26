---
title: HOW TO：調整書籤控制項的大小
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f23094aae38cb1b0dc89a2b30ab7a812d7a9cb66
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869797"
---
# <a name="how-to-resize-bookmark-controls"></a>HOW TO：調整書籤控制項的大小
  您可以在將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入 Microsoft Office Word 文件時，設定控制項的大小； 也可以稍後再調整大小。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 調整書籤大小的方法有三種：  
  
- 在 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項中加入或移除文字。  
  
   每當您在書籤中加入文字時，都會自動放大書籤，以包含新的文字。 當您刪除文字時，則會自動縮小書籤。  
  
- 變更 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 屬性。  
  
   如果變更的大小只有幾個字元，則適合這種方法。  
  
- 重新建立 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。  
  
   如果要大幅變更書籤的大小或位置，則適合這種方法。  
  
  在文件層級的專案中，您可以於設計階段或執行階段，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入專案中的文件。 在 VSTO 增益集專案中，您可以新增<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入任何開啟的文件，在執行階段。 如需詳細資訊，請參閱[＜How to：將書籤控制項加入 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>變更 start 和 end 屬性  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>在文件層級專案中，於設計階段調整書籤大小  
  
1.  選取 [屬性]  視窗中的書籤。  
  
2.  增加或減少 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 屬性的值。  
  
3.  增加或減少 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 屬性的值。  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>若要調整大小在執行階段的文件層級專案中的書籤  
  
1.  修改<xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>並<xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>屬性的<xref:Microsoft.Office.Tools.Word.Bookmark>您建立在執行階段，或在設計階段。  
  
     下列程式碼範例會將五個字元加入名為 `SampleBookmark`的書籤開頭。 這段程式碼假設書籤之前的文字至少有五個字元。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     下列程式碼範例會將五個字元加入同一個書籤的結尾。 這段程式碼假設書籤之後的文字至少有五個字元。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>若要調整大小的 VSTO 增益集專案，在執行階段中的書籤  
  
1.  修改<xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>並<xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>屬性的<xref:Microsoft.Office.Tools.Word.Bookmark>您建立在執行階段。  
  
     下列程式碼範例會建立在使用中文件第一個段落中包含文字的 <xref:Microsoft.Office.Tools.Word.Bookmark> ，然後再從 <xref:Microsoft.Office.Tools.Word.Bookmark>的開頭和結尾移除五個字元。  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>重新建立書籤  
 您可以透過加入與現有書籤同名但大小不同的新書籤，來調整文件層級專案中的書籤大小。  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>在文件層級專案中，於設計階段重新建立書籤  
  
1.  選取要包含在新 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項的文字。  
  
2.  按一下 [插入]  功能表上的 [書籤] 。  
  
3.  在 [書籤]  對話方塊中，輸入您要調整大小的書籤名稱，然後按一下 [加入] 。  
  
## <a name="see-also"></a>另請參閱  
 [如何：將書籤控制項加入 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [如何：調整 ListObject 控制項的大小](../vsto/how-to-resize-listobject-controls.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
