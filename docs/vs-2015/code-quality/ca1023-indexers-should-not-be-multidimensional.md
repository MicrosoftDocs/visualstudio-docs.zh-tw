---
title: CA1023： 不應該使用索引子多維度 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e1b1022484db26e6ff8fbc0046333f187753bb53
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588016"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023：不應該使用多維索引子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1023： 索引子不應該使用多維](https://docs.microsoft.com/visualstudio/code-quality/ca1023-indexers-should-not-be-multidimensional)。

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

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1043：必須針對索引子使用整數類或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)



