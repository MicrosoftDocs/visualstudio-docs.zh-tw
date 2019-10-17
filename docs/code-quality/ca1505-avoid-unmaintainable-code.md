---
title: CA1505：應避免撰寫無法維護的程式碼
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f39b6b909722c35edb16ebaf1cee43507f22215d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440071"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505：應避免撰寫無法維護的程式碼

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|分類|Microsoft。可維護性|
|重大變更|不中斷|

## <a name="cause"></a>原因

類型或方法的維護性指標值很低。

## <a name="rule-description"></a>規則描述

可維護性索引是使用下列計量來計算：程式程式碼、程式卷和圈複雜度。 「程式量」是一種難以瞭解的類型或方法，這是根據程式碼中的運算子和運算元數目而定。 圈複雜度是類型或方法的結構複雜度測量。 您可以在[管理程式碼的複雜度和維護性](../code-quality/code-metrics-values.md)中深入瞭解程式碼計量。

低維護性索引表示類型或方法可能很容易維護，而且很適合用來重新設計。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此違規，請重新設計類型或方法，並嘗試將它分割成較小且更具焦點的類型或方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以在無法分割類型或方法時隱藏此警告，或即使其大小很大，也會視為可維護。

## <a name="see-also"></a>請參閱

- [可維護性警告](../code-quality/maintainability-warnings.md)
- [測量受控程式碼的複雜度和維護性](../code-quality/code-metrics-values.md)
