---
title: 在字串視覺化中查看字串 |Microsoft Docs
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33e1cbd4b1c754498d7e2bd6c354e874ae8cdad5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72450390"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>在 Visual Studio 的字串視覺化中查看字串

當您在 Visual Studio 中進行調試時，您可以使用內建的字串視覺化檢視來查看字串。 字串視覺化檢視會顯示對資料提示或偵錯工具視窗而言太長的字串。 它也可以協助您識別格式錯誤的字串。

內建的字串視覺化檢視包含純文字、XML、HTML 和 JSON 選項。 您也可以從自動變數或其他偵錯工具視窗，開啟一些其他**類型的內**建視覺化檢視，例如[資料集、DataTable 和 DataView](../debugger/dataset-visualizer-dialog-box.md)物件。

> [!NOTE]
> 如果您需要在視覺化檢視中檢查 XAML 或 WPF UI 元素，請參閱或在 [調試過程中檢查 xaml 屬性](../xaml-tools/inspect-xaml-properties-while-debugging.md) ，或是 [如何使用 WPF 樹狀結構視覺化檢視](../debugger/how-to-use-the-wpf-tree-visualizer.md)。

## <a name="open-a-string-visualizer"></a>開啟字串視覺化

若要開啟字串視覺化，您必須在進行調試時暫停。 將滑鼠停留在具有純文字、XML、HTML 或 JSON 字串值的變數上，然後選取放大鏡圖示 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。

![開啟字串視覺化](../debugger/media/dbg-tips-string-visualizers.png "開啟字串視覺化")

## <a name="view-string-visualizer-data"></a>查看字串視覺化資料

在 [字串視覺化視窗] 視窗中，[ **運算式** ] 欄位會顯示您要停留在上面的變數或運算式，而 [ **值** ] 欄位則會顯示字串值。

空白 **值** 表示選擇的視覺化程式無法辨識字串。 例如， **Xml 視覺化檢視** 會顯示沒有 XML 標記之文字字串的空白 **值** ，或 JSON 字串。

若要查看所選的視覺化程式無法辨識的字串，請選擇 **文字視覺化檢視**。 **文字視覺化檢視**會顯示純文字。

### <a name="view-json-string-data"></a>查看 JSON 字串資料

格式正確的 JSON 字串會類似于下列 JSON 視覺化檢視中的圖例。 格式錯誤的 JSON 可能會顯示錯誤圖示 (或空白（如果無法辨識的) ）。 若要識別 JSON 錯誤，請將字串複製並貼到 JSON linting 工具中，例如 [JSLint](https://www.jslint.com/)。

![JSON 字串視覺化](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 字串視覺化")

### <a name="view-xml-string-data"></a>查看 XML 字串資料

格式正確的 XML 字串會類似于 XML 視覺化檢視中的下圖。 格式不正確的 XML 可能會在沒有 XML 標記的情況下顯示，如果無法辨識則為空白

![XML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-xml.png "XML 字串視覺化檢視")

### <a name="view-html-string-data"></a>查看 HTML 字串資料

格式正確的 HTML 字串會如同在瀏覽器中呈現一樣，如下圖所示。 格式錯誤的 HTML 可能會顯示為純文字。

![HTML 字串視覺化](../debugger/media/dbg-string-visualizers-html.png "HTML 字串視覺化")

## <a name="see-also"></a>另請參閱

- [建立自訂的視覺化檢視 (c #、Visual Basic) ](../debugger/create-custom-visualizers-of-data.md)
- [Visual Studio for Mac 中的資料視覺效果](/visualstudio/mac/data-visualizations)