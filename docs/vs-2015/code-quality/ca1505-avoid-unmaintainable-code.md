---
title: CA1505：避免撰寫無法維護程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f2f731b1ac0d87b59c7690d0cf57ade3570ed5f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547819"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505:應避免撰寫無法維護的程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|類別|Microsoft。可維護性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 類型或方法的維護性指標值很低。

## <a name="rule-description"></a>規則描述
 可維護性索引是使用下列計量來計算：程式程式碼、程式卷和圈複雜度。 「程式量」是一種難以瞭解的類型或方法，這是根據程式碼中的運算子和運算元數目而定。 圈複雜度是類型或方法的結構複雜度測量。 您可以在[測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)中深入瞭解程式碼計量。

 低維護性索引表示類型或方法可能很容易維護，而且很適合用來重新設計。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，請重新設計類型或方法，並嘗試將它分割成較小且更具焦點的類型或方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當類型或方法仍被視為可維護（儘管其大小很大，或無法分割類型或方法）時，請排除這個警告。

## <a name="see-also"></a>另請參閱
 可[維護性警告](../code-quality/maintainability-warnings.md) [，測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
