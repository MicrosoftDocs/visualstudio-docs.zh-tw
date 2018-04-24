---
title: CA1013：多載加號和減號運算子時必須一併多載等號比較運算子
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fd43cc3077c037b70eaa8107563bd8f40b6a096
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013：多載加號和減號運算子時必須一併多載等號比較運算子
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。

## <a name="rule-description"></a>規則描述
 型別的執行個體可以結合使用加法和減法之類的作業，您幾乎都應該定義要傳回的等號比較`true`擁有相同的構成值任何兩個執行個體。

 您無法使用預設等號比較運算子多載等號比較運算子的實作中。 這樣會導致堆疊溢位。 若要實作等號比較運算子，使用 Object.Equals 方法實作中。 請參閱下列範例。

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作等號比較運算子，使其與加法和減法運算子以數學方式一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告時的預設實作等號比較運算子提供正確的行為類型。

## <a name="example"></a>範例
 下列範例定義的類型 (`BadAddableType`) 違反此規則。 這個類型應實作等號比較運算子，讓任何兩個執行個體具有相同的欄位值測試`true`是否相等。 型別`GoodAddableType`顯示更正的實作。 請注意，此類型也不等比較運算子會實作覆寫<xref:System.Object.Equals%2A>來滿足其他規則。 也會實作完整實作<xref:System.Object.GetHashCode%2A>。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>範例
 下列範例會使用先前在本主題說明等號比較運算子的預設和正確的行為已定義的類型執行個體測試相等。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

 此範例會產生下列輸出。

 **不正確的類型: {2，2} {2，2} 相等嗎？否**
**很好的型別: {3，3} {3，3} 是否相等嗎？[是]**
**很好的型別: {3，3} {3，3} 有 = = 嗎？ [是]**
**不正確的類型: {2，2} {9,9} 相等嗎？否**
**很好的型別: {3，3} {9,9} 有 = = 嗎？ 沒有**
## <a name="see-also"></a>另請參閱
 [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)