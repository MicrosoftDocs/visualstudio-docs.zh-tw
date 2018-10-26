---
title: Ca1036： 必須覆寫在 comparable 類型的方法 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67fa52a674b9e3d77d7e3eed7493bf28c1b2514d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948763"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036：必須在 Comparable 類型中覆寫方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用或受保護的型別會實作<xref:System.IComparable?displayProperty=fullName>介面，並不會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>或沒有多載等號比較，不等比較，小於或大於的語言特定運算子。 如果型別繼承介面的實作，此規則就不會報告違規情形。

## <a name="rule-description"></a>規則描述
 定義自訂的排序順序的型別會實作<xref:System.IComparable>介面。 <xref:System.IComparable.CompareTo%2A>方法會傳回整數值，指出兩個型別執行個體的正確的排序次序。 此規則會識別設定的排序順序; 的類型這表示的相等、 不相等的一般意義小於或大於不適用。 當您提供的實作<xref:System.IComparable>，您通常必須也會覆寫<xref:System.Object.Equals%2A>使其傳回值，都必須配合<xref:System.IComparable.CompareTo%2A>。 如果您覆寫<xref:System.Object.Equals%2A>撰寫的程式碼和語言支援運算子多載，您也應該提供一致的運算子<xref:System.Object.Equals%2A>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，覆寫<xref:System.Object.Equals%2A>。 如果您的程式語言支援運算子多載，提供下列運算子：

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  在 C# 中，用來表示這些運算子的語彙基元如下所示: = =、 ！ =、 \<，和 >。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全違規起因於缺少的運算子和您的程式語言不支援運算子多載，在此情況下，使用 Visual Basic.NET 時隱藏此規則的警告。 它也是安全地隱藏這項規則的警告時它就會引發在等號比較運算子以外 op_Equality，如果您判斷實作運算子，在您的應用程式內容中毫無意義。 不過，您應該一律透過 op_Equality 與 = = 運算子，如果您覆寫 Object.Equals。

## <a name="example"></a>範例
 下列範例包含的類型，會正確地實作<xref:System.IComparable>。 程式碼註解指出方法以滿足相關的各種規則<xref:System.Object.Equals%2A>而<xref:System.IComparable>介面。

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>範例
 下列應用程式測試的行為<xref:System.IComparable>稍早所示的實作。

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [等號比較運算子](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



