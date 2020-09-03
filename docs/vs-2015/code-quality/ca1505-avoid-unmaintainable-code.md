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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547819"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505:應避免撰寫無法維護的程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|類別|Microsoft 的可維護性|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型或方法的維護性指標值很低。

## <a name="rule-description"></a>規則描述
 可維護性索引的計算方式是使用下列計量：程式程式碼、程式磁片區和圈複雜度。 程式磁片區是一種難以瞭解以程式碼中的運算子和運算元數目為基礎之類型或方法的困難之處。 迴圈複雜度是類型或方法的結構化複雜度量值。 您可以深入瞭解如何 [測量 Managed 程式碼的複雜性和可維護性的](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)程式碼度量。

 低維護性索引表示類型或方法可能很難維護，而且是重新設計的絕佳候選。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規情形，請重新設計類型或方法，並嘗試將其分割成較小且更具焦點的類型或方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當類型或方法仍視為可維護（儘管它的大小很大或無法分割類型或方法）時，請排除此警告。

## <a name="see-also"></a>另請參閱
 [測量受控碼複雜性和可維護性的](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)可[維護性警告](../code-quality/maintainability-warnings.md)
