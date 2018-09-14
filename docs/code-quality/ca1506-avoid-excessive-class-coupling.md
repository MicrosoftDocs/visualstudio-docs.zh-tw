---
title: CA1506：應避免使用結合過度的類別
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57c23ea9c6afb27ee89886936fff690a4285f5c0
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549897"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506：應避免使用結合過度的類別

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|類別|Microsoft.Maintainability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別或方法被搭配許多其他類型。

## <a name="rule-description"></a>規則描述
 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。

 類型和類別結合程度高程度的方法很難維護。 它是個不錯的做法有型別和呈現低的結合性和高一致性的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，請嘗試重新設計的類型或方法，以降低的類型，它會結合的數目。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當型別或方法仍視為可維護性，儘管其大量的其他類型的相依性時，請排除這個警告。

## <a name="see-also"></a>另請參閱

- [維護性警告](../code-quality/maintainability-warnings.md)
- [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)