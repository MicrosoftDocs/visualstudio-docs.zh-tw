---
title: CA1033：介面方法應可由子類型呼叫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee44537ba4f7f7efd65de2c8a27d139d9750b77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661870"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033：介面方法應該要可以由子類型呼叫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。

## <a name="rule-description"></a>規則描述
 請考慮明確實作為公用介面方法的基底類型。 衍生自基底類型的類型只能透過轉換成介面之目前實例（在中C#為 `this`）的參考，來存取繼承的介面方法。 如果衍生型別重新執行（明確）繼承的介面方法，就無法再存取基底執行。 透過目前實例參考的呼叫將會叫用衍生的實值;這會導致遞迴和最終堆疊溢位。

 當提供外部可見 `Close()` 或 `System.IDisposable.Dispose(Boolean)` 方法時，此規則不會報告明確執行 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 的違規。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請執行會公開相同功能的新方法，並可供衍生類型或變更 nonexplicit 的執行。 如果可接受中斷性變更，替代方法是將類型設為密封。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果提供的外部可見方法具有相同的功能，但名稱不同于明確執行的方法，則可放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型 `ViolatingBase`，以及顯示違規修正的類型 `FixedBase`。

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>請參閱
 [介面](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
