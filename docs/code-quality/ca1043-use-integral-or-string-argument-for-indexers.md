---
title: CA1043：必須針對索引子使用整數類或字串引數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad1a25f33ce91fba7b2be8723b86067afe81632c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043：必須針對索引子使用整數類或字串引數
|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用或受保護的索引子不是使用索引類型<xref:System.Int32?displayProperty=fullName>， <xref:System.Int64?displayProperty=fullName>， <xref:System.Object?displayProperty=fullName>，或<xref:System.String?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 索引子，也就是索引屬性，應該使用整數或字串類型索引。 這些類型通常用於資料結構的索引和增加的程式庫的可用性。 使用<xref:System.Object>類型應該限制為這種情況下，在設計階段無法指定特定整數或字串類型。 如果設計需要其他類型的索引，請考慮是否型別所代表的邏輯資料存放區。 如果它不代表邏輯資料存放區，使用的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將索引變更為整數或字串型別，或使用的方法而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告，只有在仔細地考量需要非標準的索引子之後。

## <a name="example"></a>範例
 下列範例將示範會使用索引子<xref:System.Int32>索引。

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1023：不應該使用多維索引子](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)