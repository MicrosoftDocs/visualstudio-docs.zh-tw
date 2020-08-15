---
title: 簡化 LINQ 運算式
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251285"
---
# <a name="simplify-linq-expression"></a>簡化 LINQ 運算式

此重構適用於：

- C#

**功能：** 針對的重構實例，以及 `SomeEnumerableType.Where(<LambdaExpression>).Single()` 下列可列舉 `SomeEnumerable.Single(<LambdaExpression>)` `Enumerable.Single()` 的方法： `SingleOrDefault()` 、 `Last()` 、 `LastOrDefault()` 、 `Any()` 、 `Count()` 、 `First()` 和 `FirstOrDefault()` 。

時機 **：** 方法呼叫、等等的所有實例都 `Single()` `SingleOrDefault()` 不會有任何引數，且前面會加上 `Where()` 運算式。 無法將運算式的輸入 `Where()` 結構化為運算式樹狀架構。

**原因：** 為方法移除不必要的呼叫， `.Where()` 可以改善效能和可讀性。

## <a name="how-to"></a>操作方式

1. 將游標放在 `SomeEnumerableType.Where(<LambdaExpression>).Single()` visual studio 中的實例內。
2. 按**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [**簡化 LINQ 運算式**]

   ![將 typeof 轉換成 nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
