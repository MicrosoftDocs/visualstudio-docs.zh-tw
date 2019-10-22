---
title: CA1013：多載運算子等於 on 多載加和減 |Microsoft Docs
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
ms.openlocfilehash: dd1c144f04150e3965e2c0264b80147cbd9b8f19
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663204"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013：多載加號和減號運算子時必須一併多載等號比較運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。

## <a name="rule-description"></a>規則描述
 當類型的實例可以使用加法和減法之類的作業結合時，您幾乎都應該針對具有相同組成值的任何兩個實例，定義傳回 `true` 的相等。

 在等號比較運算子的多載執行中，不能使用預設的等號比較運算子。 這麼做會造成堆疊溢位。 若要執行等號比較運算子，請在您的執行中使用 Equals 方法。 請參閱下列範例。

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
 若要修正此規則的違規，請執行等號比較運算子，使其在數學上與加法和減法運算子一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當等號比較運算子的預設執行提供類型的正確行為時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會定義違反此規則的類型（`BadAddableType`）。 這個型別應該會執行等號比較運算子，讓具有相同域值的兩個實例都 `true` 進行相等的測試。 類型 `GoodAddableType` 會顯示已更正的執行。 請注意，此類型也會執行不等比較運算子，並覆寫 <xref:System.Object.Equals%2A> 以滿足其他規則。 完整的執行也會執行 <xref:System.Object.GetHashCode%2A>。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>範例
 下列範例會使用先前在本主題中定義的類型實例來測試是否相等，以說明等號比較運算子的預設和正確行為。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 此範例會產生下列輸出。

 **錯誤類型： {2,2} {2,2} 相等嗎？沒有**
**良好的類型： {3,3} {3,3} 相等嗎？是**
**良好類型： {3,3} 0 是 = =？  是**1**不正確的類型： 3 4 相等嗎？沒有**5**良好的類型： 7 8 是 = =？  否**
## <a name="see-also"></a>請參閱
 [等號比較運算子](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
