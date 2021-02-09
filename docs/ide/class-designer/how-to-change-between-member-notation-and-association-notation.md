---
title: 在成員 & 關聯標記法之間變更
description: 瞭解如何將類別圖表的關聯性，從成員標記法變更為關聯標記法的類別設計工具，反之亦然。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8bc2e6c51903c46636d8de72bd6c1ac5b63aa876
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880550"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>如何：在類別設計工具中變更為成員標記法或關聯標記法

使用 [類別設計工具] 時，您可以在成員標記法與關聯標記法之間切換，以變更兩種類型在類別圖表中的關聯性代表方式。 將成員顯示為關聯線時，通常可提供類型關聯方式的實用視覺效果。

> [!NOTE]
> 您可以用成員屬性或欄位來代表關聯性。 若要將成員標記法變更為關聯標記法，某種類型必須具有其他類型的成員。 若要將關聯標記法變更為成員標記法，您必須使用關聯線來連接兩種類型。 如需詳細資訊，請參閱 [如何：建立類型之間的關聯](how-to-create-associations-between-types.md)。 如果專案包含多個類別圖表，在您變更某個圖表的關聯性顯示方式時，這些變更只會對該圖表產生影響。 若要變更其他圖表的關聯性顯示方式，請開啟或顯示該圖表，並執行下列步驟。

## <a name="to-change-member-notation-to-association-notation"></a>若要將成員標記法變更為關聯標記法

1. 從方案總管的專案中開啟類別圖表 (.cd) 檔。

2. 在類別圖表的類型圖形中，以滑鼠右鍵按一下代表關聯的成員屬性或欄位，然後選擇 [顯示為關聯]。

    > [!TIP]
    > 如果類型圖形中未顯示任何屬性或欄位，圖形區間可能已摺疊起來。 若要展開類型圖形，請按兩下區間名稱，或以滑鼠右鍵按一下類型圖形，然後選擇 [展開]。

    類型圖形區間的成員隨即消失，並出現連接兩種類型的關聯線。 關聯線會標示屬性或欄位的名稱。

## <a name="to-change-association-notation-to-member-notation"></a>若要將關聯標記法變更為成員標記法

在類別圖表中，以滑鼠右鍵按一下關聯線，然後視需要選擇 [顯示為屬性] 或 [顯示為欄位]。 關聯線隨即消失，而在圖表內該類型圖案的適當區間中會顯示屬性。

## <a name="see-also"></a>另請參閱

- [如何：建立類型之間的繼承](how-to-create-inheritance-between-types.md)
- [如何：檢視類型之間的繼承](how-to-view-inheritance-between-types.md)
- [檢視類型和關聯性](designing-and-viewing-classes-and-types.md)
- [如何：將集合關聯視覺化](how-to-visualize-a-collection-association.md)
