---
title: 書籤控制項
description: 瞭解書簽控制項是具有唯一名稱、公開事件及可系結至資料的書簽。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1da30943eff228aad3c5413c5d8faea337634e9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905267"
---
# <a name="bookmark-control"></a>書籤控制項
  <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項是具有唯一名稱、可公開事件及繫結至資料的書籤。 書籤可以做為預留位置，以標記 Microsoft Office Word 文件中的項目或位置。 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項是 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件和 <xref:Microsoft.Office.Interop.Word.Range> 物件的組合。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 在文件層級的專案中，您可以在設計階段或執行階段，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入文件。 在 VSTO 增益集專案中，您可以於執行階段將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入任何開啟的文件。 如需詳細資訊，請參閱 [如何：將書簽控制項新增至 Word 檔](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。

## <a name="bind-data-to-the-control"></a>將資料系結至控制項
 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項支援簡單資料繫結。 書籤應該使用 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 屬性繫結至資料來源。 書籤的預設資料繫結屬性是 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性。

 如果已更新系結資料集中的資料， <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項會顯示變更。

 在文件層級專案中，您也可以使用 [資料來源]  視窗，將資料繫結至書籤。 如需詳細資訊，請參閱 [如何：在檔中填入物件的資料](../vsto/how-to-populate-documents-with-data-from-objects.md)。

## <a name="formatting"></a>格式化
 可套用至 <xref:Microsoft.Office.Interop.Word.Bookmark> 的格式，也可套用至 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。 此格式包括字型、縮排、間距、編號和樣式。

## <a name="assign-text-to-the-bookmark"></a>將文字指派給書簽
 <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> 物件與 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> 控制項之間還有另一個差異，那就是指派文字給書籤的行為不同。 如果您將文字指派給長度為零的 <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>，則會將文字附加至書籤右側，且書籤的長度會保持為零。 不過，如果您將文字指派給長度為零的 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>，則會將文字插入書籤，且書籤的長度會延長為插入的字元總數。

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> 控制項也有 <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> 屬性。 這個屬性與 <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> 控制項屬性（property）或物件的屬性（property）上可用的屬性（property）不同 <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> 。

|Text 屬性|Description|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|使用這個屬性可顯示書籤內的文字，並將書籤保留在文件上。 指派文字給書籤會擴充書籤範圍，但不會刪除書籤。<br /><br /> 例如， `Bookmark1.Text = "Hello world"` 會將文字插入書籤，並保留完整的書籤。|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|使用這個屬性可顯示書籤位置上的文字，並自動刪除書籤。 例如， `Bookmark1.Range.Text = "Hello world"` 會將文字插入書籤，並刪除書籤。|

## <a name="rename-the-control-at-design-time"></a>在設計階段重新命名控制項
 在文件層級專案中，當您將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項從 [工具箱]  拖曳至文件時，Visual Studio 會自動產生該控制項的名稱。 您可以在 [屬性]  視窗中，變更控制項的名稱。

## <a name="overlapping-controls"></a>重迭的控制項
 書簽控制項可以互相重迭。 相同的文字可以由一個以上的書簽共用。 當您將新文字指派給其中一個重迭的書簽時，它只會包含新的文字，而且書簽不會再重迭。 另一個書簽現在只會包含未在原始重迭書簽之間共用的文字。

 下表顯示 "This is sample text." 一句如何 由兩個重迭的書簽共用：

|書籤|Text|
|--------------|----------|
|重疊書籤|[this is {sample] text.}|
|Bookmark1|This is sample|
|Bookmark2|sample text.|

 如果您指派新文字 "This is replacement" 若要 Bookmark1，書簽不會重迭，Bookmark2 只會保留原本不是 Bookmark1 一部分的文字。

|書籤|Text|
|--------------|----------|
|兩個獨立書籤|[this is replacement]{ text.}|
|Bookmark1|This is replacement|
|Bookmark2|text.|

如果您變更包含另一個書簽的書簽文字，則不會刪除內部書簽。 不過，內部書簽會變成空的書簽，並移至外部書簽的結尾。

下表顯示 "This is sample text." 一句如何 是由包含在另一個書簽內的書簽所共用：

|書籤|Text|
|--------------|----------|
|重疊書籤|[this is {sample} text.]|
|Bookmark1|This is sample text.|
|Bookmark2|sample|

 如果您指派新文字 "This is replacement" 給 Bookmark1，這些書籤將不再互相重疊，且 Bookmark2 會成為位於 Bookmark1 尾端的空白書籤。

|書籤|Text|
|--------------|----------|
|兩個獨立書籤|[這是取代的。]{}|
|Bookmark1|This is replacement.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>事件

下列事件適用於 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項：

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>另請參閱

- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [如何：將書簽控制項新增至 Word 檔](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [逐步解說：建立書簽的快捷方式功能表](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)