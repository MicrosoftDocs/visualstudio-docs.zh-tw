---
title: HOW TO：實作介面 (類別設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e76aeea4c6779e97d882705e8680cd7a3b00d129
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975173"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>HOW TO：在類別設計工具中實作介面

在 [類別設計工具] 中，您可以將介面連線至替介面方法提供程式碼的類別，以在類別圖表上實作介面。 [類別設計工具] 會產生介面實作，並將介面和類別之間的關聯性顯示為繼承關聯性。 您可以在介面與類別之間繪製繼承線，或從 [類別檢視] 中拖曳介面，來實作介面。

> [!TIP]
> 您可以像建立其他類型一樣建立介面。 如果介面存在，但未出現在類別圖表上，請先顯示它。 如需詳細資訊，請參閱[如何：使用類別設計工具建立類型](how-to-create-types.md)和[如何：檢視現有類型](how-to-view-existing-types.md)。

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>繪製繼承線來實作介面

1. 在類別圖表上，顯示介面和將實作介面的類別。

2. 從類別和介面繪製繼承線。

     會顯示棒棒糖符號，附加至類別，並且具有介面名稱的標籤會識別繼承關聯性。 Visual Studio 會為所有介面成員產生虛設常式。

如需詳細資訊，請參閱[如何：建立類型之間的繼承](how-to-create-inheritance-between-types.md)。

## <a name="to-implement-an-interface-from-the-class-view-window"></a>從 [類別檢視] 視窗實作介面

1. 在類別圖表上，顯示您要實作介面的類別。

2. 開啟 [類別檢視]，並找出此介面。

    > [!TIP]
    > 如果未開啟 [類別檢視]，請從 [檢視] 功能表開啟 [類別檢視] 或按 **Ctrl**+**Shift**+**C**。

3. 將介面節點拖曳到圖表上的類別圖形。

     會顯示棒棒糖符號，附加至類別，並且具有介面名稱的標籤會識別繼承關聯性。 Visual Studio 會為所有介面成員產生虛設常式。此時，即已實作介面。

## <a name="see-also"></a>另請參閱

- [如何：使用類別設計工具建立類型](how-to-create-types.md)
- [如何：檢視現有類型](how-to-view-existing-types.md)
- [如何：建立類型之間的繼承](how-to-create-inheritance-between-types.md)
- [重構類別與類型](refactoring-classes-and-types.md)