---
title: 如何：建立基本 Phong 著色器
description: 瞭解如何使用著色器設計工具和有向圖形著色器語言，來建立可實作為傳統 Phong 光源模型的光源著色器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5319526da9aa59951729389749e53f3df65b643
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915720"
---
# <a name="how-to-create-a-basic-phong-shader"></a>如何：建立基本 Phong 著色器

本文會示範如何使用著色器設計工具和有向圖著色器語言 (DGSL) 來建立光源的著色器，實作傳統的 Phong 光源模型。

## <a name="the-phong-lighting-model"></a>Phong 光源模型

Phong 光源模型擴充 Lambert 光源模型以納入反射強光，模擬表面的反射屬性。 反射元件可從用於 Lambert 光源模型的定向光源提供其他的照明，但對完稿色彩的比重則有不同的處理方式。 反射強光會根據檢視方向、光源方向及表面方向之間的關係，對場景中的各個表面有不同影響。 其為表面的反射色彩、光澤度和方向以及光源的色彩、濃度和方向的產物。 向檢視器直接反射光源的表面會得到最大的反射比重，而會反射使光源遠離檢視器的表面則不會得到任何比重。 在 Phong 光源模型下，可結合一或多個反射元件，來決定物件上各點的反射強光色彩和濃度，然後再加入 Lambert 光源模型的結果，以產生像素的完稿色彩。

如需 Lambert 光源模型的詳細資訊，請參閱[如何：建立基本 Lambert 著色器](../designers/how-to-create-a-basic-lambert-shader.md)。

開始之前，請確定已顯示 [屬性] 視窗和 [工具箱]。

1. 建立 Lambert 著色器，如[如何：建立基本 Lambert 著色器](../designers/how-to-create-a-basic-lambert-shader.md)中所述。

2. 中斷 [Lambert]節點和 [完稿色彩]節點的連接。 選擇 [Lambert] 節點的 [RGB] 端點，然後選擇 [中斷連結]。 這樣會替下一個步驟加入的節點留出空間。

3. 將 [加入] 節點加入圖形。 在 [工具箱] 的 [數學] 下，選取 [加入]，並將其移至設計介面。

4. 將 [反射] 節點加入圖形。 在 [工具箱] 的 [工用程式] 下，選取 [反射]，並將其移至設計介面。

5. 加入反射比重。 將 [反射] 節點的 [輸出] 端點移至 [加入] 節點的 [X] 端點，然後將 [Lambert] 節點的 [輸出] 端點移至 [加入] 節點的 [Y] 端點。 這些連接結合像素的總擴散和反射色彩比重。

6. 將計算後的色彩值連接到完稿色彩。 將 [加入] 節點的 [輸出] 端點移至 [完稿色彩] 節點的 [RGB] 端點。

   下圖顯示完成的著色器圖形和套用至茶壺模型的著色器預覽。

> [!NOTE]
> 為了更適當展現此圖中的著色器效果，已使用著色器的 **MaterialDiffuse** 參數來指定橘色，並使用 **MaterialSpecular** 和 **MaterialSpecularPower** 參數來指定金屬外觀。 如需材質參數的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜預覽著色器＞一節。

![著色器圖形及其效果預覽](../designers/media/digit-lighting-graph.png)

某些圖形可對一些著色器提供更佳的預覽。 如需如何在著色器設計工具中預覽著色器的詳細資訊，請參閱[著色器設計](../designers/shader-designer.md)工具中的預覽著色器區段

下圖顯示本文件中所述套用至 3D 模型的著色器。 將 **MaterialSpecular** 屬性設定為 (1.00, 0.50, 0.20, 0.00)，並將其 **MaterialSpecularPower** 屬性設定為 16。

> [!NOTE]
> **MaterialSpecular** 屬性可決定表面材質的外觀。 一種高光面表面，例如往往有亮白色反射色彩的玻璃或塑膠板。 金屬表面常會有接近其擴散色彩的反射色彩。 緞面表面往往會有深灰色的反射色彩。
>
> **MaterialSpecularPower** 屬性可決定反射亮部的濃度。 高光澤度會模擬更模糊、範圍更小的亮部。 非常低的光澤度會模擬強烈、呈彎曲狀的亮部，使整個表面的色彩過度飽和而隱蔽起來。

![已套用至模型的 Phong 光源](../designers/media/digit-lighting-model.png)

如需如何將著色器套用至 3D 模型的詳細資訊，請參閱[如何：將著色器套用至 3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)。

## <a name="see-also"></a>另請參閱

- [如何：將著色器套用至3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [如何：匯出著色器](../designers/how-to-export-a-shader.md)
- [如何：建立基本 Lambert 著色器](../designers/how-to-create-a-basic-lambert-shader.md)
- [著色器設計工具](../designers/shader-designer.md)
- [著色器設計工具節點](../designers/shader-designer-nodes.md)
