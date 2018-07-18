---
title: 書籤控制項
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 60ab9db37f3ed41de4afcdecbf2c9e83ffb5c2f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264008"
---
# <a name="bookmark-control"></a>書籤控制項
  <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項是具有唯一名稱、可公開事件及繫結至資料的書籤。 書籤可以做為預留位置，以標記 Microsoft Office Word 文件中的項目或位置。 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項是 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件和 <xref:Microsoft.Office.Interop.Word.Range> 物件的組合。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 在文件層級專案中，您可以加入<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件在設計階段或執行階段。 在 VSTO 增益集專案中，您可以加入<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入任何開啟的文件，在執行階段。 如需詳細資訊，請參閱[如何： 加入書籤控制項加入 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。

## <a name="bind-data-to-the-control"></a>資料繫結至控制項
 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項支援簡單資料繫結。 書籤應該使用 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 屬性繫結至資料來源。 書籤的預設資料繫結屬性是 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性。

 如果更新繫結資料集中，<xref:Microsoft.Office.Tools.Word.Bookmark>控制項顯示的變更。

 在文件層級專案中，您也可以使用 [資料來源]  視窗，將資料繫結至書籤。 如需詳細資訊，請參閱[How to： 從物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)。

## <a name="formatting"></a>格式化
 可套用至 <xref:Microsoft.Office.Interop.Word.Bookmark> 的格式，也可套用至 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。 此格式包括字型、 縮排、 間距、 編號，和樣式。

## <a name="assign-text-to-the-bookmark"></a>指派文字給書籤
 其他的差異<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>物件和<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>控制項是指派文字給書籤時，它的運作方式。 如果您將文字指派給長度為零<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>、 將文字附加至書籤右側，以及書籤保留長度為零。 不過，如果您將文字指派給長度為零<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>、 將文字插入書籤和書籤的長度會延長為插入的字元總數。

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>控制項也有<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>屬性。 這個屬性是不同於<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>屬性上提供<xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType>屬性<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>控制項，或<xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType>屬性<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>物件。

|Text 屬性|描述|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|使用這個屬性可顯示書籤內的文字，並將書籤保留在文件上。 指派文字給書籤會擴充書籤範圍，但不會刪除書籤。<br /><br /> 例如， `Bookmark1.Text = "Hello world"` 會將文字插入書籤，並保留完整的書籤。|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|使用這個屬性可顯示書籤位置上的文字，並自動刪除書籤。 例如， `Bookmark1.Range.Text = "Hello world"` 會將文字插入書籤，並刪除書籤。|

## <a name="rename-the-control-at-design-time"></a>在設計階段重新命名控制項
 在文件層級專案中，當您將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項從 [工具箱]  拖曳至文件時，Visual Studio 會自動產生該控制項的名稱。 您可以在 [屬性]  視窗中，變更控制項的名稱。

## <a name="overlapping-controls"></a>重疊控制項
 書籤控制項可以互相重疊。 多個書籤可以共用相同的文字。 當您將新文字指派給其中一個重疊書籤時，它包含新的文字，並不會再重疊書籤。 其他書籤現在會包含原始重疊書籤之間未共用的文字。

 下表顯示 "This is sample text." 一句如何 由兩個重疊書籤所共用：

|書籤|Text|
|--------------|----------|
|重疊書籤|[this is {sample] text.}|
|Bookmark1|This is sample|
|Bookmark2|sample text.|

 如果您指派新文字 "This is replacement" 給 Bookmark1，這些書籤不會重疊，且 Bookmark2 會保留未原本屬於 Bookmark1 的文字。

|書籤|Text|
|--------------|----------|
|兩個獨立書籤|[this is replacement]{ text.}|
|Bookmark1|This is replacement|
|Bookmark2|text.|

如果您變更包含另一個書籤的書籤的文字，內部書籤不會遭到刪除。 不過，內部書籤會變成空白書籤，並移至外部書籤的結尾。

下表顯示 "This is sample text." 一句如何 包含在另一個書籤的書籤所共用：

|書籤|Text|
|--------------|----------|
|重疊書籤|[this is {sample} text.]|
|Bookmark1|This is sample text.|
|Bookmark2|範例|

 如果您指派新文字 "This is replacement" 給 Bookmark1，這些書籤將不再互相重疊，且 Bookmark2 會成為位於 Bookmark1 尾端的空白書籤。

|書籤|Text|
|--------------|----------|
|兩個獨立書籤|[this is replacement]{}|
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

## <a name="see-also"></a>另請參閱

- [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [如何： 將書籤控制項加入 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [逐步解說： 建立書籤的捷徑功能表](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)