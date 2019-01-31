---
title: HOW TO：建立灰階紋理著色器
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58f6ca03a7bad27ad3c2cb4f7dae662e14292e95
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015502"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>HOW TO：建立灰階紋理著色器

本文會示範如何使用著色器設計工具和有向圖形著色器語言 (DGSL)，來建立灰階紋理著色器。 這個著色器可修改材質範例的 RGB 色彩值，然後和未經修改的 Alpha 值一起使用來設定完稿色彩。

## <a name="create-a-grayscale-texture-shader"></a>建立灰階紋理著色器

您可以在寫入完稿輸出色彩之前，修改材質範例的色彩值，來實作灰階材質著色器。

開始之前，請確定已顯示 [屬性] 視窗和 [工具箱]。

1.  建立基本紋理著色器，如[如何：建立基本紋理著色器](../designers/how-to-create-a-basic-texture-shader.md)中所述。

2.  將 [材質範例] 節點的 [RGB] 端點和 [完稿色彩] 節點的 [RGB] 端點中斷連接。 在 [選取] 模式中，選擇 [材質範例] 節點的 [RGB] 端點，然後選擇 [中斷連結]。 這樣會替下一個步驟加入的節點留出空間。

3.  將 [反滲透] 節點加入圖形。 在 [工具箱] 的 [篩選] 下，選取 [反滲透]，並將其移至設計介面。

4.  使用 [反滲透] 節點來計算灰階值。 在 [選取] 模式中，將 [材質範例] 節點的 [RGB] 端點移至 [反滲透] 節點的 [RGB] 端點。

    > [!NOTE]
    > 根據預設，[反滲透] 節點可將輸入色彩完全去色，並使用標準的明亮度加權進行灰階轉換。 您可以變更 [明亮度] 屬性的值或只將輸入色彩部分去色，來變更 [反滲透] 節點的行為。 若要將輸入色彩部份去色，請對 [反滲透] 節點的 [百分比] 端點提供 [0, 1] 範圍內的純量值。

5.  將灰階色彩值連接到完稿色彩。 將 [反滲透] 節點的 [輸出] 端點移至 [完稿色彩] 節點的 [RGB] 端點。

下圖顯示完成的著色器圖形和套用至立方體的著色器預覽。

> [!NOTE]
> 在此圖中，使用一個平面當成預覽圖形，並已指定材質以更適當展現著色器的效果。

![著色器圖形及其效果預覽](../designers/media/digit-grayscale-effect.png)

某些圖形可對一些著色器提供更佳的預覽。 如需在著色器設計工具中預覽著色器的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)

## <a name="see-also"></a>另請參閱

- [如何：將著色器套用至 3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [如何：匯出著色器](../designers/how-to-export-a-shader.md)
- [Image Editor](../designers/image-editor.md)
- [著色器設計工具](../designers/shader-designer.md)
- [著色器設計工具節點](../designers/shader-designer-nodes.md)