---
title: CA1023：索引子不應為多維度 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30eee67d54e4fc3c73b265240fff82b0729e1cfc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546641"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023:不應該使用多維索引子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含使用一個以上索引的公用或受保護索引子。

## <a name="rule-description"></a>規則描述
 索引子（也就是索引的屬性）應該使用單一索引。 多維度索引子可能會大幅降低程式庫的可用性。 如果設計需要多個索引，請重新考慮類型是否代表邏輯資料存放區。 如果不是，請使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將設計變更為使用單獨的整數或字串索引，或使用方法，而不是索引子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請只在仔細考慮非標準索引子的需求之後，才隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示型別， `DayOfWeek03` 其中包含違反規則的多維度索引子。 索引子可以視為轉換類型，因此會更適當地公開為方法。 類型已在中重新設計 `RedesignedDayOfWeek03` ，以符合規則。

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1043:必須針對索引子使用整數或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024:建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)
