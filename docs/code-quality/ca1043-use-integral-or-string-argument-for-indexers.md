---
title: CA1043:必須針對索引子使用整數或字串引數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ae1d75341a857d380f78a2b8c0532fcdad1f5e1b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987587"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043:必須針對索引子使用整數或字串引數

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用或受保護的索引子使用的索引類型以外<xref:System.Int32?displayProperty=fullName>， <xref:System.Int64?displayProperty=fullName>， <xref:System.Object?displayProperty=fullName>，或<xref:System.String?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 索引子，也就是索引的屬性，應該使用整數或字串類型索引。 這些類型通常會用於編製索引的資料結構，而且增加程式庫的可用性。 使用<xref:System.Object>類型應該限制為這種情況下，在設計階段無法指定特定的整數或字串類型。 如果設計需要其他類型的索引，請重新考慮類型是否表示的邏輯資料存放區。 如果它不代表邏輯資料存放區，使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更索引的整數或字串類型，或使用的方法，而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏這項規則只有在仔細地考量需要非標準的索引子之後的警告。

## <a name="example"></a>範例
 下列範例示範使用索引子<xref:System.Int32>索引。

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1023:索引子不應該使用多維](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024:在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)