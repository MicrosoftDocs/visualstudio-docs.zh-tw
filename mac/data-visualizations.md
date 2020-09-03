---
title: 偵錯 - 資料視覺效果
description: 偵錯是程式設計當中常見且必要的一部分。 Visual Studio for Mac 包含整個套件的功能，可讓偵錯變容易。 本篇文章探討在偵錯工具中檢查物件時，可檢視的不同資料視覺效果。
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 14696040160dfc33f89b7647fb73b116b41afa16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67691736"
---
# <a name="data-visualizations"></a>資料視覺效果

Visual Studio for Mac 包含支援偵錯工具的 UI，允許在偵錯時將變數、欄位或屬性值視覺化。 這些資料視覺化檢視會顯示資料的擴充版本，且可讓開發人員檢查已知的結構，例如顯示色彩結構的色彩。

若要顯示偵錯**本機**板中的視覺化工具，只要按一下使用者停留在資料列上時出現在值右邊的預覽圖示即可：

![本機板](media/data-visualizations-image9.png)

下列清單列出在 Visual Studio for Mac 中進行偵錯時可用的許多新視覺效果。

## <a name="point"></a>Point
Point/PointF 或 iOS 和 Mac 中的 CGPoint，會在偵錯板中轉譯為顯示 X 和 Y 值的 Tuple：

![點視覺效果](media/data-visualizations-image10.png)

## <a name="size"></a>Size
Size/SizeF 或 iOS 和 Mac 中的 CGSize 會轉譯為矩形。 將進行繪製以擴展直到尺寸的增長超過 250 px 為止，此時會將矩形擴展為最大尺寸 250 px：

[大小視覺效果](media/data-visualizations-image11.png)

## <a name="rectangle"></a>矩形
Rectangle/RectangleF 或 iOS 和 Mac 的 CGRect 會顯示尺寸和原點。 與大小類似，將會進行繪製以擴展直到尺寸的增長超過 250 px 為止：

![矩形視覺效果](media/data-visualizations-image12.png)

## <a name="coordinate"></a>座標
座標會繪製在地圖上，並將位置釘選到中央：

[座標視覺效果](media/data-visualizations-image13.png)

## <a name="color"></a>色彩
這會顯示 UIColor、CGColor 和 Color 屬性，用來描述彩色預覽、RGBA 元件、色調-飽和-亮度值和色彩的十六進位值：

![色彩視覺效果](media/data-visualizations-image14.png)

## <a name="images"></a>影像

媒體呈現時最多擴展為最大尺寸 250 px，並且將在影像超過 250 px 時進行縮放以符合大小：

![影像視覺效果](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>貝茲曲線

視覺化檢視將顯示 `NSBezierPath`：

![貝茲曲線視覺效果](media/data-visualizations-image16.png)

## <a name="string"></a>String

少於 100 個字元的字串會完整顯示，而不進行預覽。 較長的字串會在預覽中完整顯示。 字串可進行編輯，且視覺化檢視會伴隨顯示 [編輯] 按鈕，讓您能夠在預覽或字串值編輯器中編輯字串值，如下所示：

![字串視覺效果](media/data-visualizations-image17.png)

### <a name="small-strings"></a>小型字串：
![小型字串視覺效果](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>中等長度字串：
![中度字串視覺效果](media/data-visualizations-image19.png)

### <a name="editor"></a>編輯器：

![編輯器視覺效果](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable 會列舉所有值；透過按一下 [顯示值]**** 按鈕，即可檢視每個 IEnumerable 的值。 IEnumerable 選項不會顯示物件 (例如 `Array`、`ArrayList`、`List<>`、`Dictionary<,>`) 的值，因為它們具有自己的偵錯工具視覺化檢視。

![IEnumerable 視覺效果](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>其他視覺化檢視

也有自己的內嵌視覺化檢視的其他某些類型如下：

![其他視覺效果](media/data-visualizations-image23.png)

* **基本型別**
  * 這會顯示基本類型的原始值。
* **列舉**
  * 這會顯示不含 enum 類型限定詞的欄位值。
* **元**
  * 以格式 (,) 顯示
* **Null**
  * 顯示 "null" 值。
* **URL**
  * 這會顯示可按式超連結。
* **IntPtr**
  * 這會顯示 IntPtr 的十六進位表示法。

## <a name="see-also"></a>另請參閱

- [檢查 [自動] 視窗和 [本機] 視窗中的變數 (Windows 上的 Visual Studio)](/visualstudio/debugger/autos-and-locals-windows)
- [檢視視覺化檢視中的字串 (Windows 上的 Visual Studio)](/visualstudio/debugger/string-visualizer-dialog-box)