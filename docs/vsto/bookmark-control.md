---
title: "書籤控制項 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 38e3286d24f0591ca4ced3339118b6d0d4bfe1d7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="bookmark-control"></a>書籤控制項
  <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項是具有唯一名稱、可公開事件及繫結至資料的書籤。 書籤可以做為預留位置，以標記 Microsoft Office Word 文件中的項目或位置。 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項是 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件和 <xref:Microsoft.Office.Interop.Word.Range> 物件的組合。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 在文件層級的專案中，您可以在設計階段或執行階段，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入文件。 在 VSTO 增益集專案中，您可以在執行階段將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入任何開啟的文件。 如需詳細資訊，請參閱 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。  
  
## <a name="binding-data-to-the-control"></a>將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項支援簡單資料繫結。 書籤應該使用 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 屬性繫結至資料來源。 書籤的預設資料繫結屬性是 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性。  
  
 如果更新繫結資料集中的資料，則 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項會反映這些變更。  
  
 在文件層級專案中，您也可以使用 [資料來源]  視窗，將資料繫結至書籤。 如需詳細資訊，請參閱 [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md)。  
  
## <a name="formatting"></a>格式化  
 可套用至 <xref:Microsoft.Office.Interop.Word.Bookmark> 的格式，也可套用至 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。 這包括字型、縮排、間距、編號方式和樣式。  
  
## <a name="assigning-text-to-the-bookmark"></a>指派文字給書籤  
 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件與 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項之間還有另一個差異，那就是指派文字給書籤的行為不同。 如果您將文字指派給長度為零的 <xref:Microsoft.Office.Interop.Word.Bookmark>，則會將文字附加至書籤右側，且書籤的長度會保持為零。 不過，如果您將文字指派給長度為零的 <xref:Microsoft.Office.Tools.Word.Bookmark>，則會將文字插入書籤，且書籤的長度會延長為插入的字元總數。  
  
 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項也有 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性。 這與 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> 屬性或 <xref:Microsoft.Office.Tools.Word.Bookmark> 物件的 <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> 屬性上提供的 <xref:Microsoft.Office.Interop.Word.Bookmark> 屬性不同。  
  
|Text 屬性|描述|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|使用這個屬性可顯示書籤內的文字，並將書籤保留在文件上。 指派文字給書籤會擴充書籤範圍，但不會刪除書籤。<br /><br /> 例如， `Bookmark1.Text = "Hello world"` 會將文字插入書籤，並保留完整的書籤。|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|使用這個屬性可顯示書籤位置上的文字，並自動刪除書籤。 例如， `Bookmark1.Range.Text = "Hello world"` 會將文字插入書籤，並刪除書籤。|  
  
## <a name="renaming-the-control-at-design-time"></a>在設計階段重新命名控制項  
 在文件層級專案中，當您將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項從 [工具箱]  拖曳至文件時，Visual Studio 會自動產生該控制項的名稱。 您可以在 [屬性]  視窗中，變更控制項的名稱。  
  
## <a name="overlapping-controls"></a>重疊控制項  
 書籤控制項可以互相重疊；也就是說，多個書籤可以共用相同的文字。 當您將新文字指派給其中一個重疊書籤時，它只會包含新文字，且書籤將不再互相重疊。 其他書籤現在只會包含原始重疊書籤之間未共用的文字。  
  
 下表顯示 "This is sample text." 一句如何 由兩個重疊書籤所共用。  
  
|書籤|Text|  
|--------------|----------|  
|重疊書籤|[this is {sample] text.}|  
|Bookmark1|This is sample|  
|Bookmark2|sample text.|  
  
 如果您指派新文字 "This is replacement" 給 Bookmark1，這些書籤將不再互相重疊，且 Bookmark2 只會保留原本屬於 Bookmark1 的文字。  
  
|書籤|Text|  
|--------------|----------|  
|兩個獨立書籤|[this is replacement]{ text.}|  
|Bookmark1|This is replacement|  
|Bookmark2|text.|  
  
 如果某個書籤完全包含在另一個書籤內，而且您變更了外部書籤的文字，並不會刪除內部書籤。 不過，內部書籤會成為空白書籤並移至外部書籤尾端。 下表顯示 "This is sample text." 一句如何 由包含在另一個書籤的書籤所共用。  
  
|書籤|Text|  
|--------------|----------|  
|重疊書籤|[this is {sample} text.]|  
|Bookmark1|This is sample text.|  
|Bookmark2|範例|  
  
 如果您指派新文字 "This is replacement" 給 Bookmark1，這些書籤將不再互相重疊，且 Bookmark2 會成為位於 Bookmark1 尾端的空白書籤。  
  
|書籤|Text|  
|--------------|----------|  
|兩個獨立書籤|[this is replacement.]{}|  
|Bookmark1|This is replacement.|  
|Bookmark2|*\<空白 >*|  
  
## <a name="events"></a>事件  
 下列事件適用於 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項：  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>請參閱  
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [逐步解說： 建立書籤的捷徑功能表](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  