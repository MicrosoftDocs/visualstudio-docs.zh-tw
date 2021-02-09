---
title: 繪製圖案與路徑
description: 您可以使用 Blend for Visual Studio 中的 XAML 設計工具功能來繪製路徑和圖形、修改它們，以及將它們合併。
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e815b3e4959727dab282fcbe0fcd1f82890bf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847345"
---
# <a name="draw-shapes-and-paths"></a>繪製圖案與路徑

在 XAML 設計工具中，「圖形」(Shape) 正如您所預期。 例如：矩形、圓形或橢圓形。 *「路徑」* (path) 是圖形的更靈活版本。 您可以執行像是調整形狀，或將圖形合併在一起形成新的圖形等動作。

圖形與路徑使用向量圖形，因此可以配合高解析度顯示妥善調整。

## <a name="draw-a-shape"></a>繪製圖形

在 [資產] 視窗中尋找圖形。

:::image type="content" source="media/blend-shapes.png" alt-text="Blend for Visual Studio 中 [資產] 視窗的 [圖形] 類別的螢幕擷取畫面":::

將您想要的任何圖形拖曳至畫板。 然後，使用圖形上的控點來調整、旋轉、移動或扭曲圖形。

![處理](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>繪製路徑

路徑是一系列連接的直線和曲線。 使用路徑來建立 [資產] 視窗中所沒有的有趣圖形。

您可以使用線條、畫筆或鉛筆來繪製路徑。 您可以在 [工具] 視窗中找到這些工具。

### <a name="draw-a-straight-line"></a>繪製直線

使用 [畫筆] 工具或 [線條] 工具。

**使用 [畫筆] 工具**

在畫板上，按一次可定義起始點，然後再按一次可定義線條的結尾。

**使用 [線條] 工具**

在畫板上，從想要讓線條開始的地方拖曳起，然後再於想要線條結束的點上放開。

### <a name="draw-a-curve"></a>繪製曲線

使用 [畫筆] 工具。

在畫板上，按一次可定義線條的起始點，然後按一下並拖曳指標可建立所需的曲線。

如果您想要關閉路徑，請按一下線條的第一個點。

### <a name="change-the-shape-of-a-curve"></a>變更曲線的形狀

使用 [直接選取] 工具。

按一下圖形，然後拖曳圖形上的任一點可變更曲線圖形。

### <a name="draw-a-free-form-path"></a>繪製任意形狀的路徑

使用 [鉛筆] 工具。

在畫板上，繪製任意形狀的路徑，就像使用真正的鉛筆一樣。

### <a name="remove-part-of-a-path"></a>移除路徑的一部分

使用 [直接選取] 工具。

選取包含所要刪除線段的路徑，然後按一下 [刪除]  按鈕。

### <a name="remove-a-point-in-a-path"></a>移除路徑中的點

使用 [選取] 工具來選取路徑。 然後，使用 [畫筆] 工具來按一下您想要移除的點。

### <a name="add-a-point-to-a-path"></a>將點加入至路徑

使用 [選取] 工具來選取路徑。 使用 [畫筆] 工具來按一下路徑上您要新增點的任何位置。

## <a name="convert-a-shape-to-a-path"></a>將圖形轉換成路徑

若要以修改路徑的相同方式來修改圖形，請將圖形轉換為路徑。 選取圖形，然後選取 [   >    >  **轉換成路徑** 的格式路徑]。

**觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png) [Working with paths: Convert a shape to a path](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147) (使用路徑：將圖形轉換成路徑)。

> [!NOTE]
> [轉換成路徑] 目前不適用於 `TargetPlatformVersion` 至少為 10.0.16299.0 或更新版本的 UWP 應用程式。

## <a name="combine-paths"></a>合併路徑

您可以將路徑與圖形合併為單一路徑。

![合併路徑](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Number|動作|
|-|-|
|![合併前的兩個圖形](../designers/media/b1_1.png)|合併前的兩個圖形|
|![聯集](../designers/media/b1_2.png)|聯集|
|![除以](../designers/media/b1_3.png)|除以|
|![Intersect](../designers/media/b1_4.png)|Intersect|
|![排除重疊](../designers/media/b1_5.png)|排除重疊|
|![減去](../designers/media/b1_6.png)|減去|

**觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png) [Working with paths: Combine paths](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195) (使用路徑：合併路徑)。

## <a name="create-a-compound-path"></a>建立複合路徑

當您建立複合路徑時，這些路徑的任何交集部分都會從結果中減去，而所產生的路徑會採用最底層路徑的視覺屬性。

您可以在建立複合路徑之後隨時打散這些路徑。

![中斷複合路徑](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png) [Working with paths: Create a compound path](https://www.youtube.com/watch?v=Io5bC0-nH6Q) (使用路徑：建立複合路徑)。

## <a name="create-a-clipping-path"></a>建立裁剪路徑

裁剪路徑是套用至其他物件的路徑或圖形，隱藏了所遮蔽物件落於裁剪路徑外面的部分。

![裁剪路徑](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png) [Working with paths: Create a clipping path](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232) (使用路徑：建立裁剪路徑)。
