---
title: CA1506：避免過度類別耦合 |Microsoft Docs
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
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545700"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506:應避免使用結合過度的類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|類別|Microsoft 的可維護性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型或方法與許多其他類型結合。

## <a name="rule-description"></a>規則描述
 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。

 具有高度類別結合程度的類型和方法可能難以維護。 最好的方法是具有低結合性和高一致性的類型和方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，請嘗試重新設計類型或方法，以減少其結合的類型數目。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當類型或方法仍視為可維護（儘管其他類型的相依性很多）時，請排除此警告。

## <a name="see-also"></a>另請參閱
 [測量受控碼複雜性和可維護性的](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)可[維護性警告](../code-quality/maintainability-warnings.md)
