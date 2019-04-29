---
title: 字串視覺化檢視對話方塊 |Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 982db296fd17fb86b4a139e02a9418eeb507cd91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902519"
---
# <a name="string-visualizer-dialog-box"></a>[字串視覺化檢視] 對話方塊

雖然您正在偵錯在 Visual Studio 中，您可以使用內建字串視覺化檢視中檢視字串。 字串視覺化檢視會顯示資料提示或偵錯工具視窗太長的字串。 它也可協助您識別格式不正確的字串。

內建字串視覺化檢視包含純文字、 XML、 HTML 和 JSON 選項。 您也可以開啟 內建的視覺化檢視針對幾個其他類型，例如[DataSet、 DataTable 和 DataView](../debugger/dataset-visualizer-dialog-box.md)物件，從**自動變數**或其他偵錯工具視窗。

> [!NOTE]
> 如果您需要檢查視覺化檢視中的 XAML 或 WPF UI 項目，請參閱或[偵錯時檢查 XAML 屬性](../debugger/inspect-xaml-properties-while-debugging.md)或是[如何使用 WPF 樹狀架構視覺化檢閱](../debugger/how-to-use-the-wpf-tree-visualizer.md)。

若要開啟字串視覺化檢視，您必須在偵錯期間將其暫停。 將滑鼠停在具有純文字、 XML、 HTML 或 JSON 字串值，然後選取放大鏡圖示的變數![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。

## <a name="uielement-list"></a>UIElement 清單

**運算式**欄位會顯示變數或您要將滑鼠停留的運算式。

**值**欄位顯示的字串值。 空白**值**表示所選的視覺化檢視無法辨識字串。 例如， **XML 視覺化檢視**會顯示空白**值**沒有的 XML 標記的文字字串或 JSON 字串。 若要檢視所選的視覺化檢視無法辨識的字串，請選擇**文字視覺化檢視**改。 **文字視覺化檢視**顯示純文字。

### <a name="json-string-data"></a>JSON 字串資料

語式正確的 JSON 字串看起來會像下圖中的 JSON 視覺化檢視。 格式不正確的 JSON 可能會顯示錯誤圖示 （或如果無法辨識的空白）。 若要識別 JSON 錯誤，將複製並貼在字串 JSON linting 工具這類[JSLint](https://www.jslint.com/)。

![JSON 字串視覺化檢視](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 字串視覺化檢視")

### <a name="xml-string-data"></a>XML 字串資料

語式正確的 XML 字串看起來會像下圖中 XML 視覺化檢視。 如果無法辨識的格式不正確的 XML 可能會顯示不含 XML 標記或空白。

![XML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-xml.png "XML 字串視覺化檢視")

### <a name="html-string-data"></a>HTML 字串資料

出現的語式正確的 HTML 字串一樣呈現在瀏覽器中，如下圖所示。 格式不正確的 HTML 可能會顯示為純文字。

![HTML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-html.png "HTML 字串視覺化檢視")

## <a name="see-also"></a>另請參閱

- [建立自訂視覺化檢視 （C#、 Visual Basic）](../debugger/create-custom-visualizers-of-data.md)
- [在 Visual Studio for Mac 中的資料視覺效果](/visualstudio/mac/data-visualizations)