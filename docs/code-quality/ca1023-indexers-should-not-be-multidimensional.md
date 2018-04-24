---
title: CA1023：不應該使用多維索引子
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: 876eb79237b843721b71a1879cfbb83e7a9918db
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023：不應該使用多維索引子
|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用或受保護的索引子使用一個以上的索引。

## <a name="rule-description"></a>規則描述
 索引子，也就是索引屬性，應使用單一索引。 多維索引子會大幅降低程式庫的可用性。 如果設計需要多個索引，請考慮是否型別所代表的邏輯資料存放區。 否則，請使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更為使用單獨的整數或字串索引設計或使用的方法而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告，只有在仔細地考量需要非標準的索引子之後。

## <a name="example"></a>範例
 下列範例顯示型別， `DayOfWeek03`，與違反規則的多維索引子。 索引子被視為一種轉換，因此更適當地公開為方法。 中的類型經過重新設計`RedesignedDayOfWeek03`以符合下列規則。

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1043：必須針對索引子使用整數類或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)