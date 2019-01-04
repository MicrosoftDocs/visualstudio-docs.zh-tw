---
title: CA1023:不應該使用多維索引子
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2e1282612da884dfbaff646a3b84f713ada7ed75
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852621"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023:不應該使用多維索引子

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用或受保護的索引子，會使用一個以上的索引。

## <a name="rule-description"></a>規則描述
 索引子，也就是索引的屬性，應該使用單一索引。 多維索引子可以大幅降低程式庫的可用性。 如果設計需要多個索引，請重新考慮類型是否表示的邏輯資料存放區。 否則，請使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更設計，以使用獨立的整數或字串的索引，或使用的方法，而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏這項規則只有在仔細地考量需要非標準的索引子之後的警告。

## <a name="example"></a>範例
 下列範例示範一個型別， `DayOfWeek03`，違反規則多維索引子。 索引子可以視為一種轉換，因此更適當地公開為方法。 型別在重新設計`RedesignedDayOfWeek03`來滿足的規則。

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1043： 必須使用索引子的整數類或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024:在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)