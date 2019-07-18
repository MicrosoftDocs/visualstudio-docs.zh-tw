---
title: CA1501:避免在物件間過度繼承
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d77ecc255f03e38e39a9321d9c7a9e5568e94a4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546332"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501:避免在物件間過度繼承

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|分類|Microsoft.Maintainability|
|中斷變更|中斷|

## <a name="cause"></a>原因

類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。

## <a name="rule-description"></a>規則描述

太深的巢狀類型階層架構可能會難以依循、了解和維護。 此規則會限制分析，以在相同的模組中的階層。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，從較深的階層架構中的基底類型衍生的型別，或排除某些中繼的基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告。 不過，程式碼可能會更難維護。 請注意，根據基底類型的可見性，解決違反此規則可能會產生重大變更。 比方說，移除公用基底型別是一項重大變更。

## <a name="example"></a>範例

下列範例顯示違反規則的型別：

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]