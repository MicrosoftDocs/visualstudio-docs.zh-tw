---
title: 類別設計工具中的 c + + 列舉
description: 瞭解類別設計工具如何支援 c + + 列舉和範圍列舉類別類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b12d270884ca9877d6c1c80780a9ae96324f3af4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903451"
---
# <a name="c-enumerations-in-class-designer"></a>類別設計工具中的 c + + 列舉

[類別設計工具] 支援 C++ `enum` 和範圍 `enum class` 類型。 以下是範例：

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

類別圖表中的 C++ 列舉圖形外觀和運作方式與結構圖形類似，不同之處在於標籤為「列舉」或「列舉類別」、它是粉紅色而不是藍色，而且它的左和上邊界具有有色框線。 列舉圖形和結構圖形都有方角。

如需使用 `enum` 類型的詳細資訊，請參閱[列舉](/cpp/cpp/enumerations-cpp)。

## <a name="see-also"></a>另請參閱

- [使用 c + + 程式碼](working-with-visual-cpp-code.md)
- [列舉](/cpp/cpp/enumerations-cpp)
