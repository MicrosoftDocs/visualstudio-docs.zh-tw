---
title: CA1036 必須：覆寫可比較類型上的方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779e6258f9c5be256a7973a5d917045507fc82e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661832"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036：必須在 Comparable 類型中覆寫方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用或受保護的類型會實 <xref:System.IComparable?displayProperty=fullName> 介面，且不會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName> 或不會針對等號、不等、小於或大於，將語言特定的運算子多載。 如果類型只繼承介面的執行，此規則就不會報告違規。

## <a name="rule-description"></a>規則描述
 定義自訂排序次序的類型會執行 <xref:System.IComparable> 介面。 @No__t_0 方法會傳回整數值，表示類型的兩個實例的正確排序次序。 此規則會識別設定排序次序的類型;這表示不適用相等、不等、小於和大於的一般意義。 當您提供 <xref:System.IComparable> 的執行時，通常也必須覆寫 <xref:System.Object.Equals%2A>，使其傳回與 <xref:System.IComparable.CompareTo%2A> 一致的值。 如果您覆寫 <xref:System.Object.Equals%2A>，而且是以支援運算子多載的語言撰寫程式碼，您也應該提供與 <xref:System.Object.Equals%2A> 一致的運算子。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請覆寫 <xref:System.Object.Equals%2A>。 如果您的程式設計語言支援運算子多載，請提供下列運算子：

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  在C#中，用來表示這些運算子的標記如下： = =、！ =、\< 和 >。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當違規是因為遺漏運算子而造成，而您的程式設計語言不支援運算子多載時，可以安全地隱藏此規則的警告，如同 Visual Basic .NET 的情況。 如果您判斷在應用程式內容中執行運算子並不合理，則在 op_Equality 以外的等號比較運算子上引發時，也可以安全地隱藏此規則的警告。 不過，如果您覆寫了 Object.equals，您應該一律高於 op_Equality 和 = = 運算子。

## <a name="example"></a>範例
 下列範例包含可正確執行 <xref:System.IComparable> 的類型。 程式碼批註會識別符合與 <xref:System.Object.Equals%2A> 和 <xref:System.IComparable> 介面相關之各種規則的方法。

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>範例
 下列應用程式會測試稍早所示之 <xref:System.IComparable> 執行的行為。

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>請參閱
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [等號比較運算子](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
