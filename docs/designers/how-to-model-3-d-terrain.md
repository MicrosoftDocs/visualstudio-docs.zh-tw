---
title: 如何：建立 3D 地形模型
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a863834790683b229c17ad55b9930a2b382c027b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589418"
---
# <a name="how-to-model-3d-terrain"></a>如何：建立 3D 地形模型

本文會示範如何使用模型編輯器來建立 3D 地形模型。

## <a name="create-a-3d-terrain-model"></a>建立 3D 地形模型

您可以細分平面建立額外的表面，然後操控其頂點以建立想要的地形特徵來建立 3D 地形。

當您完成時，結果應該像這樣：

![顯示地形模型的 3D 場景](../designers/media/digit-terrain-model.png)

開始之前，請確定已顯示 [屬性] 視窗和 [工具箱]。

1. 建立要使用的 3D 模型。 如需如何將模型新增至專案的資訊，請參閱[模型編輯器](../designers/model-editor.md)中的＜使用者入門＞一節。

2. 將平面加入場景。 在 [工具箱] 的 [形狀] 下，選取 [平面]，並將其移至設計介面。

    > [!TIP]
    > 您可以在設計介面中框架處理平面物件，使其更容易使用。 在 [選取] 模式中，選取平面物件，然後在 [模型編輯器] 工具列上，選擇 [框架物件] 按鈕。

3. 進入表面選取模式。 在 [模型編輯器] 工具列上，選擇 [選取表面]。

4. 細分該平面。 在表面選取模式中，選擇平面一次，啟動選擇功能，然後再次選擇以選取其唯一的表面。 在 [模型編輯器] 工具列上，選擇 [細分表面]。 這樣會在平面加入新的頂點，分割成大小均一的四個部分。

5. 建立多個子區塊。 讓新的表面仍處於選取狀態，選擇 [細分表面] 兩次。 這樣會建立總計 64 個表面。 藉由建立多個子區塊，您可以提供更細部的地形。

6. 進入點選取模式。 在 [模型編輯器] 工具列上，選擇 [選取點]。

7. 修改點以建立地形特徵。 在點選取模式，選取其中一點，然後在 [模型編輯器] 工具列上，選擇 [平移] 工具。 設計介面上隨即出現代表該點的方塊。 您可以使用綠色箭頭來移動方塊，並藉此修改點的高度。 對不同點重複此步驟，來建立想要的地形特徵。

    > [!TIP]
    > 您可以一次選取數個點來統一修改。

完成地形模型。 以下顯示套用 Phong 網底的最終模型︰

![顯示地形模型的 3D 場景](../designers/media/digit-terrain-model.png)

您可以使用此地形模型來展現漸層著色器的效果，如[如何：建立以幾何為基礎的漸層著色器](../designers/how-to-create-a-geometry-based-gradient-shader.md)中所述。

## <a name="see-also"></a>請參閱

- [模型編輯器](../designers/model-editor.md)
