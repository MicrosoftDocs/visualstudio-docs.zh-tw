---
title: CA1043 必須：針對索引子使用整數或字串引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 528b3a1f301544ccb20cfa6bddc31c0a5c50d1ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668294"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043：必須針對索引子使用整數類或字串引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含使用 <xref:System.Int32?displayProperty=fullName>、<xref:System.Int64?displayProperty=fullName>、<xref:System.Object?displayProperty=fullName> 或 <xref:System.String?displayProperty=fullName> 以外之索引類型的公用或受保護索引子。

## <a name="rule-description"></a>規則描述
 索引子（也就是索引的屬性）應該使用整數或字串類型做為索引。 這些類型通常用於編制資料結構的索引，並增加程式庫的可用性。 只有在設計階段無法指定特定整數或字串類型的情況下，才應限制使用 <xref:System.Object> 類型。 如果設計需要其他類型的索引，請重新考慮類型是否代表邏輯資料存放區。 如果它不代表邏輯資料存放區，請使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將索引變更為整數或字串類型，或使用方法，而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請只在仔細考慮非標準索引子的需求之後，才隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示使用 <xref:System.Int32> 索引的索引子。

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1023：不應該使用多維索引子](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)
