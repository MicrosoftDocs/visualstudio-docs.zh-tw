---
title: 類別設計工具中的 Visual C++ 列舉 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651657"
---
# <a name="visual-c-enumerations-in-class-designer"></a>類別設計工具中的 Visual C++ 列舉類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

類別設計工具支援 C++ `enum` 和範圍 `enum class` 類型。 以下是一個範例：

```
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

 類別圖表中的 C++ 列舉圖形外觀和運作方式與結構圖形類似，不同之處在於標籤為「列舉」  或「列舉類別」  、它是粉紅色而不是藍色，而且它的左和上邊界具有有色框線。 列舉圖形和結構圖形都有方角。

 如需使用 `enum` 類型的詳細資訊，請參閱[列舉](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)。

## <a name="see-also"></a>另請參閱
 [使用 Visual C++ Code （類別設計工具） ](../ide/working-with-visual-cpp-code-class-designer.md) [Enumerations](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)
