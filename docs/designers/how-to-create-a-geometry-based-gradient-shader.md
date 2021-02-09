---
title: 如何：建立以幾何為基礎的漸層著色器
description: 瞭解如何使用著色器設計工具和有向圖形著色器語言，來建立以幾何為基礎的漸層著色器，以調整常數 RGB 色彩值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f3814eabb38e205acedd6bd2b00fd98901568c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931028"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>如何：建立以幾何為基礎的漸層著色器

本文會示範如何使用著色器設計工具和有向圖形著色器語言，來建立以幾何為基礎的漸層著色器。 這個著色器可透過世界空間中物件各點的高度，來縮放 RGB 色彩常數值。

## <a name="create-a-geometry-based-gradient-shader"></a>建立以幾何為基礎的漸層著色器

您可以將像素位置納入著色器，來實作以幾何為基礎的著色器。 在著色語言中，像素包含的資訊不只有其在 2D 螢幕上的色彩與位置資訊。 在某些系統中稱為「片段」的像素是一組值集合，描述對應於像素的表面。 本文件中所述的著色器會利用世界空間中 3D 物件每個像素的高度，影響片段的完稿輸出色彩。

開始之前，請確定已顯示 [屬性] 視窗和 [工具箱]。

1. 建立要使用的 DGSL 著色器。 如需有關如何將 DGSL 著色器加到專案的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜使用者入門＞一節。

2. 中斷 [點色彩]節點和 [完稿色彩]節點的連接。 選擇 [點色彩] 節點的 [RGB] 端點，然後選擇 [中斷連結]。 這樣會替下一個步驟加入的節點留出空間。

3. 將 [乘積] 節點加入圖形。 在 [工具箱] 的 [數學] 下，選取 [乘積]，並將其移至設計介面。

4. 將 [遮罩向量] 節點加入圖形。 在 [工具箱] 的 [工用程式] 下，選取 [遮罩向量]，並將其移至設計介面。

5. 指定 [遮罩向量] 節點的遮罩值。 在 [選取] 模式中，選取 [遮罩向量] 節點，然後在 [屬性] 視窗中，將 [綠色/ Y] 設定為 [True]，並將 [紅色/ X]、[藍色/ Z] 及 [Alpha / W] 設定為 [False]。 在此範例中，[紅色 / X]、[綠色 / Y] 及 [藍色 / Z] 屬性會對應到 [世界空間位置] 節點的 x、 y 及 z 分量，而且未使用 [Alpha / W]。 因為只有 [綠色 / Y] 設為 [True]，所以加上遮罩之後，只剩下輸入向量的 y 分量。

6. 將 [世界空間位置] 節點加入圖形。 在 [工具箱] 的 [常數] 下，選取 [世界空間位置]，然後將其移至設計介面。

7. 為片段的世界空間位置加上遮罩。 在 [選取] 模式中，將 [世界空間位置] 節點的 [輸出] 端點移至[ 遮罩向量] 節點的 [向量] 端點。 此連接會為該片段的位置加上遮罩，以忽略 x 和 z 分量。

8. 將 RGB 色彩常數乘以遮罩的世界空間位置。 將 [點色彩] 節點的 [RGB] 端點移至 [乘積] 節點的 [Y] 端點，然後將 [遮罩向量] 節點的 [輸出] 端點移至 [乘積] 節點的 [X] 端點。 此連接會依據世界空間中的像素高度來調整色彩值。

9. 將調整的色彩值連接到完稿色彩。 將 [乘積] 節點的 [輸出] 端點移至 [完稿色彩] 節點的 [RGB] 端點。

下圖顯示完成的著色器圖形和套用至圓球的著色器預覽。

> [!NOTE]
> 在本圖例中，指定橘色以更適當展現著色器效果，但因為世界空間中尚無預覽圖形的位置，而無法在著色器設計工具中完整預覽著色器。 著色器必須在實際場景中預覽，才能呈現完整的效果。

![著色器圖形及其效果預覽](../designers/media/digit-gradient-effect-graph.png)

某些圖形可對一些著色器提供更佳的預覽。 如需如何在著色器設計工具中預覽著色器的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜預覽著色器＞。

下圖顯示本文件中所述的著色器，套用至[如何：建立 3D 地形模型](../designers/how-to-model-3-d-terrain.md)中所示的 3D 場景。 色彩濃度會隨著世界空間的點高度增加。

![已套用至 3D 地形模型的漸層效果](../designers/media/digit-gradient-effect-result.png)

如需如何將著色器套用至 3D 模型的詳細資訊，請參閱[如何：將著色器套用至 3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)。

## <a name="see-also"></a>另請參閱

- [如何：將著色器套用至3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [如何：匯出著色器](../designers/how-to-export-a-shader.md)
- [如何：建立3D 地形模型](../designers/how-to-model-3-d-terrain.md)
- [如何：建立灰階材質著色器](../designers/how-to-create-a-grayscale-texture-shader.md)
- [著色器設計工具](../designers/shader-designer.md)
- [著色器設計工具節點](../designers/shader-designer-nodes.md)
