---
title: 簡化 LINQ 運算式
description: 這項重構可用來移除 Where 方法之可列舉的不必要呼叫。
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466163"
---
# <a name="simplify-linq-expression"></a>簡化 LINQ 運算式

此重構適用於：

- C#

事項 **：** 的重構實例，以及 `SomeEnumerableType.Where(<LambdaExpression>).Single()` 下列可列舉 `SomeEnumerable.Single(<LambdaExpression>)` `Enumerable.Single()` 的方法： `SingleOrDefault()` 、 `Last()` 、 `LastOrDefault()` 、 `Any()` 、 `Count()` 、 `First()` 和 `FirstOrDefault()` 。

時機 **：** 方法呼叫、等的所有實例都沒有 `Single()` `SingleOrDefault()` 任何引數，而且前面會加上 `Where()` 運算式。 運算式的輸入 `Where()` 無法以運算式樹狀架構的形式來構成。

**原因：** 移除對可列舉方法的不必要呼叫，可 `.Where()` 改善效能和可讀性。

## <a name="how-to"></a>使用方法

1. 將游標放在 `SomeEnumerableType.Where(<LambdaExpression>).Single()` visual studio 的實例內。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
3. Select **簡化 LINQ 運算式**

   ![將 typeof 轉換為 nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
