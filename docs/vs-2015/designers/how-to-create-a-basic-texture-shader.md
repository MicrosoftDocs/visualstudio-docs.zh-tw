---
title: 如何：建立基本材質著色器 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59a926ab35e04aa120bc57250c3e5b2712858aa5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664491"
---
# <a name="how-to-create-a-basic-texture-shader"></a>如何：建立基本材質著色器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用著色器設計工具和有向圖形著色器語言 (DGSL)，來建立單一材質著色器。 這個著色器會將完稿色彩直接設定為從材質中取樣 RGB 和 Alpha 值。

 本文件示範下列活動︰

- 移除著色器圖形中的節點

- 將節點加入圖形

- 設定著色器參數

- 設定參數可見度

- 連接節點

## <a name="creating-a-basic-texture-shader"></a>建立基本材質著色器
 您可以直接將材質範例的色彩與 Alpha 值直接寫入完稿輸出色彩，來實作基本的單一材質著色器。

 開始之前，請確定已顯示 [屬性]  視窗和 [工具箱]  。

#### <a name="to-create-a-basic-texture-shader"></a>建立基本材質著色器

1. 建立要使用的 DGSL 著色器。 如需有關如何將 DGSL 著色器加到專案的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜使用者入門＞一節。

2. 刪除 [點色彩]  節點。 在 [選取]  模式中，選取 [點色彩]  節點，然後在功能表列上，選取 [編輯]  、[刪除]  。 這樣會替下一個步驟加入的節點留出空間。

3. 將 [材質範例]  節點加入圖形。 在 [工具箱]  的 [材質]  下，選取 [材質範例]  ，並將其移至設計介面。

4. 將 [材質座標]  節點加入圖形。 在 [工具箱]  的 [材質]  下，選取 [材質座標]  ，並將其移至設計介面。

5. 選擇要套用的材質。 在 [選取]  模式中，選取 [材質範例]  節點，然後在 [屬性]  視窗中，使用 [檔名]  屬性來指定您想要使用的材質。

6. 將材質設為可公開存取。 選取 [材質範例]  節點，然後在 [屬性]  視窗中，將 [存取權]  屬性設定 [公用]  。 現在您可以從另一個工具設定材質，例如 [模型編輯器]  。

7. 將材質座標連接到材質範例。 在 [選取]  模式中，將 [材質座標]  節點的 [輸出]  端點移至 [材質範例]  節點的 [UV]  端點。 此連接會對指定座標的材質取樣。

8. 將材質範例連接到完稿色彩。 將 [材質範例]  節點的 [RGB]  端點移至 [完稿色彩]  節點的 [RGB]  端點，然後將 [材質範例]  節點的 [Alpha]  端點移至 [完稿色彩]  節點的 [Alpha]  端點。

   下圖顯示完成的著色器圖形和套用至立方體的著色器預覽。

> [!NOTE]
> 在此圖中，使用一個平面當成預覽圖形，並已指定材質以更適當展現著色器的效果。

 ![著色器圖形及其效果預覽](../designers/media/digit-texture-effect.png "|::ref1::|")

 某些圖形可對一些著色器提供更佳的預覽。 如需如何在著色器設計工具中預覽著色器的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)

## <a name="see-also"></a>另請參閱
 [如何：將著色器套用至3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)[影像編輯器](../designers/image-editor.md)[著色](../designers/shader-designer.md)器設計工具[著色器節點](../designers/shader-designer-nodes.md)
