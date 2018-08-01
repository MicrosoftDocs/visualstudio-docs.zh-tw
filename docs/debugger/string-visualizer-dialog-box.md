---
title: 字串視覺化檢視中檢視字串 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6e4519a85659b36e5cf6baebaadd1d1c626f1a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151030"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>在 Visual Studio 中的字串視覺化檢視中檢視字串
當您偵錯時，您可以開啟字串視覺化檢視，以檢視字串太長，無法在資料提示或偵錯工具視窗中檢視。 在許多情況下，視覺化檢視，也可協助您識別格式不正確的字串。

標準的內建字串視覺化檢視會包含純文字、 XML、 HTML 和 JSON。 Windows 像一些其他類型設定，例如偵錯工具中顯示的 WPF 物件**自動變數** 視窗中，您也可以開啟視覺化檢視。

## <a name="open-a-string-visualizer"></a>開啟字串視覺化檢視

若要檢視純文字、 XML、 HTML 或 JSON 字串，請按一下 放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")將滑鼠移到包含字串值的變數。 您必須先暫停偵錯工具若要查看的放大鏡圖示。

![開啟字串視覺化檢視](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>檢視字串資料

**運算式**字串視覺化檢視中的欄位會在偵錯工具中顯示 「 目前的變數或運算式您暫留。

**值**欄位顯示的字串值。 文字視覺化檢視會顯示純文字。

空白**值**指出特定的視覺化檢視無法辨識字串類型。 例如，XML 視覺化檢視會顯示空白**值**適用於簡單的文字字串 （使用任何 XML 標記） 或 JSON 格式化字串。 如果您需要為無法辨識字串在視覺化檢視中，使用 文字視覺化檢視。

### <a name="view-json-string-data"></a>檢視 JSON 字串資料

語式正確的 JSON 字串會出現類似下圖中的 JSON 視覺化檢視。 格式不正確的 JSON 可能會顯示錯誤圖示 （或如果無法辨識的空白）。 如果您看到錯誤圖示時，複製並將 JSON 字串貼到 JSON linting 工具這類[JSLint](https://www.jslint.com/)找出 JSON 時發生錯誤。

![JSON 字串視覺化檢視](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 字串視覺化檢視")

### <a name="view-xml-string-data"></a>檢視 XML 的字串資料

語式正確的 XML 字串會出現類似下圖中 XML 視覺化檢視。 格式不正確的 XML 可能會顯示不含 XML 標記 （或如果無法辨識的空白）。

![XML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-xml.png "XML 字串視覺化檢視")

### <a name="view-html-string-data"></a>檢視 HTML 字串資料

語式正確的 HTML 字串看起來會像您會看到字串，是否要呈現在瀏覽器中，如下圖所示的檢視。 格式不正確的 HTML 可能會顯示為純文字。

![HTML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-html.png "HTML 字串視覺化檢視")

## <a name="see-also"></a>另請參閱  
 [建立自訂視覺化檢視 （C#、 Visual Basic）](../debugger/create-custom-visualizers-of-data.md)