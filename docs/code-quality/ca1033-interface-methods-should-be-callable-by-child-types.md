---
title: CA1033:介面方法應該要可以由子類型呼叫
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0ed38a713f9e9a2ab95ad7e1062c6d5d9ab541d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236097"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033:介面方法應該要可以由子類型呼叫

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因
非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。

## <a name="rule-description"></a>規則描述
請考慮明確實作為公用介面方法的基底類型。 衍生自基底類型的類型只能透過轉換成介面之目前實例（`this`在中C#）的參考，來存取繼承的介面方法。 如果衍生的型別實作（明確）繼承的介面方法，就無法再存取基底實作為。 透過目前實例參考的呼叫將會叫用衍生的實值;這會導致遞迴和最終堆疊溢位。

當提供外部可見<xref:System.IDisposable.Dispose%2A?displayProperty=fullName> `Close()`或`System.IDisposable.Dispose(Boolean)`方法時，此規則不會報告明確執行的違規。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請執行會公開相同功能的新方法，並可供衍生類型或變更 nonexplicit 的執行。 如果可接受中斷性變更，替代方法是將類型設為密封。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果提供的外部可見方法具有相同的功能，但名稱不同于明確執行的方法，則可放心地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的類型`ViolatingBase`，以及會顯示違規修正的`FixedBase`類型。

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>另請參閱
[介面](/dotnet/csharp/programming-guide/interfaces/index)