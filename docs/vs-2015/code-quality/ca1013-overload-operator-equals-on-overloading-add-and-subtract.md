---
title: CA1013：多載的運算子 equals 在多載的加法和減法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545414"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013:多載加號和減號運算子時必須一併多載等號比較運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。

## <a name="rule-description"></a>規則描述
 當可以使用加法和減法之類的運算來結合型別的實例時，您幾乎都應該 `true` 針對擁有相同組成值的兩個實例定義相等。

 您無法在等號比較運算子的多載執行中使用預設的等號比較運算子。 這樣做會導致堆疊溢位。 若要執行等號比較運算子，請在您的實中使用物件. Equals 方法。 請參閱下列範例。

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
 若要修正此規則的違規情形，請執行等號比較運算子，使其與加法和減法運算子具有數學一致性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當相等運算子的預設實作為型別的正確行為時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例 `BadAddableType` 會定義違反此規則 () 類型。 此類型應該會執行等號比較運算子，讓具有相同域值的兩個實例都能測試 `true` 是否相等。 此類型會 `GoodAddableType` 顯示已更正的實作為。 請注意，此型別也會執行不等比較運算子和覆寫 <xref:System.Object.Equals%2A> 來滿足其他規則。 完整的實施也會執行 <xref:System.Object.GetHashCode%2A> 。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>範例
 下列範例會使用先前在本主題中定義的類型實例來測試是否相等，以說明相等運算子的預設和正確行為。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 此範例會產生下列輸出。

 **錯誤的類型： {2,2} {2,2}相等嗎？沒有** 
 **正確的類型： {3,3} {3,3} 等於嗎？是** 
 **好的類型： {3,3} {3,3} 是 = =？  是** 
 **不正確的類型： {2,2} {9,9} 等於嗎？沒有** 
 **正確的類型： {3,3} {9,9} 是 = =？  否**
## <a name="see-also"></a>另請參閱
 [等號比較運算子](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
