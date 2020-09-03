---
title: CA1033：介面方法應該可由子類型呼叫 |Microsoft Docs
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
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542294"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033:介面方法應該要可以由子類型呼叫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。

## <a name="rule-description"></a>規則描述
 請考慮明確實作為公用介面方法的基底類型。 從基底型別衍生的型別只能透過 `this` 轉換成介面的 c # )  (目前實例的參考，來存取繼承的介面方法。 如果衍生型別重新實 (明確) 繼承的介面方法，則無法再存取基底實作為。 透過目前實例參考的呼叫將會叫用衍生的實值。這會造成遞迴和最終堆疊溢位。

 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>當提供外部可見或方法時，此規則不會報告明確執行的 `Close()` 違規 `System.IDisposable.Dispose(Boolean)` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請執行公開相同功能的新方法，並可在衍生類型或 nonexplicit 執行變更時看見。 如果可接受中斷性變更，替代方法是將類型設為密封。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果提供的外部可見方法具有相同的功能，但名稱與明確執行的方法不同，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別， `ViolatingBase` 以及 `FixedBase` 會顯示違規修正的型別。

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>另請參閱
 [介面](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
