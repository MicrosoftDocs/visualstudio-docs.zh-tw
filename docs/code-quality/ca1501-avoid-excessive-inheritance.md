---
title: CA1501：避免過度繼承
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
ms.openlocfilehash: fceabd5487b28d4cf16b5cc0d61cd81de2aeb23a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444155"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501：避免過度繼承

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|分類|Microsoft。可維護性|
|重大變更|中斷|

## <a name="cause"></a>原因

類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。

## <a name="rule-description"></a>規則描述

太深的巢狀類型階層架構可能會難以依循、了解和維護。 此規則會將分析限制為相同模組中的階層。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請從在繼承階層架構中較不深層的基底類型衍生類型，或排除部分中繼基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以放心地隱藏此規則的警告。 不過，程式碼可能比較不容易維護。 請注意，根據基底類型的可見度，解決此規則的違規可能會建立中斷性變更。 例如，移除公用基底類型是一種中斷變更。

## <a name="example"></a>範例

下列範例顯示違反規則的類型：

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]
