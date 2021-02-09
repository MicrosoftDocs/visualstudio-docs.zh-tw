---
title: 如何：修改 3D 模型的樞紐點
description: 瞭解如何使用模型編輯器來修改3D 模型的軸點，也就是定義旋轉和縮放物件中心的點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4eaa3d671a8c9aeb3ed942e57278160af73dec19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930833"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>如何：修改 3D 模型的樞紐點

本文示範如何使用模型編輯器來修改 3D 模型的「樞紐點」。 樞紐分析點是空間中的點，定義物件在旋轉和縮放時的數學中心。

## <a name="modify-the-pivot-point-of-a-3d-model"></a>修改 3D 模型的樞紐點

您可以修改 3D 模型的樞紐分析點，以重新定義其原點。

請確定已顯示 [屬性] 視窗和 [工具箱]。

1. 從現有的3D 模型開始，例如 [如何：建立基本3d 模型](../designers/how-to-create-a-basic-3-d-model.md)中所述。

2. 進入樞紐分析模式。 在 [模型編輯器模式] 工具列上，選擇 [樞紐分析表模式] 按鈕以啟動樞紐分析表模式。 出現在 [樞紐分析表模式] 按鈕附近的方塊，指出 [模型編輯器] 現在處於樞紐分析表模式。 在樞紐分析表模式中，像是平移的作業會影響物件的樞紐分析點，而不是世界空間中的物件結構。

3. 修改物件的樞紐分析點。 在 [選取] 模式中，選取該物件，然後在 [模型檢視器] 工具列上，選擇 [平移] 工具。 設計介面上隨即出現代表樞紐分析點的方塊。 移動該方塊以修改物件的樞紐分析點。

     您可以透過移動方塊，在 3D 空間中移動樞紐分析點。 若要沿著某一座標軸平移樞紐分析點，請移動對應至該軸的箭頭。 方塊和箭頭會變成黃色，指出受到平移影響的座標軸。

     您也可以使用 [屬性] 視窗中的 [ 在空間中移動樞紐位置] 屬性，來指定樞紐分析點。

    > [!TIP]
    > 您可以旋轉物件來檢視新樞紐分析點的效果。 若要加以旋轉，請使用 [旋轉] 工具或修改 [旋轉] 屬性。

以下模型具有已修改的樞紐點：

![具有已修改之樞紐點的房屋模型](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>另請參閱

- [如何：建立基本3D 模型](../designers/how-to-create-a-basic-3-d-model.md)
- [模型編輯器](../designers/model-editor.md)
