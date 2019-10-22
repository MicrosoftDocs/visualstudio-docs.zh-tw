---
title: CA1506：避免過度的類別結合 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e85ac61e404ac9bc1afb9459716c2395233c5080
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607398"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506：應避免使用結合過度的類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft。可維護性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型或方法與許多其他類型結合。

## <a name="rule-description"></a>規則描述
 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。

 具有高程度類別結合的類型和方法可能很容易維護。 最佳做法是讓類型和方法呈現低耦合和高一致性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，請嘗試重新設計類型或方法，以減少它所結合的類型數目。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當類型或方法仍被視為可維護時，請排除這項警告，儘管其他類型的相依性很多。

## <a name="see-also"></a>請參閱
 可[維護性警告](../code-quality/maintainability-warnings.md) [，測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
