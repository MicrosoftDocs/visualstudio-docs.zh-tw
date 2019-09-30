---
title: CA1506:應避免使用結合過度的類別
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234487"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506:應避免使用結合過度的類別

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|分類|Microsoft.Maintainability|
|重大變更|中斷|

## <a name="cause"></a>原因

類型或方法與許多其他類型結合。

## <a name="rule-description"></a>規則描述

這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。

具有高程度類別結合的類型和方法可能很容易維護。 有一個很好的作法，就是讓型別和方法展現低耦合和高一致性。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此違規，請嘗試重新設計類型或方法，以減少其結合的類型數目。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

當類型或方法被視為可維護時，不論其他類型的相依性有多大，請排除這個警告。

## <a name="see-also"></a>另請參閱

- [維護性警告](../code-quality/maintainability-warnings.md)
- [測量 Managed 程式碼的複雜度和維護性](../code-quality/code-metrics-values.md)