---
title: "Ca1036： 必須覆寫方法在 comparable 類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9c8eedd58df2665b9e00051e40a07a0ac226ec6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036：必須在 Comparable 類型中覆寫方法
|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的型別會實作<xref:System.IComparable?displayProperty=fullName>介面，並不會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>或沒有多載是否相等，不等、 小於或大於的語言特定比較運算子。 此規則不會報告違規情形，如果型別繼承介面的實作。  
  
## <a name="rule-description"></a>規則描述  
 定義自訂排序順序的型別會實作<xref:System.IComparable>介面。 <xref:System.IComparable.CompareTo%2A>方法會傳回整數值，指出兩個型別執行個體的正確的排序次序。 此規則會識別類型設定排序順序。這表示，一般意義等號比較、 不等、 小於或大於不適用。 當您提供的實作<xref:System.IComparable>，您通常必須也覆寫<xref:System.Object.Equals%2A>，使它傳回一致的有效值<xref:System.IComparable.CompareTo%2A>。 如果您覆寫<xref:System.Object.Equals%2A>及在撰寫程式碼中支援運算子多載的語言，您也應該提供一致的運算子<xref:System.Object.Equals%2A>。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請覆寫<xref:System.Object.Equals%2A>。 如果您的程式語言支援運算子多載，提供下列運算子：  
  
-   op_Equality  
  
-   op_Inequality  
  
-   op_LessThan  
  
-   op_GreaterThan  
  
 在 C# 中，用來代表這些運算子的語彙基元如下: = =、 ！ =、 \<，和 >。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它是安全違規因遺漏的運算子和您的程式語言不支援運算子多載中，使用 Visual Basic.NET 案例時隱藏此規則的警告。 它也是安全地隱藏此規則的警告時引發的等號比較運算子以外 op_Equality，如果您決定實作運算子的應用程式內容中毫無意義。 不過，您應一律透過 op_Equality，如果您覆寫 Object.Equals = = 運算子。  
  
## <a name="example"></a>範例  
 下列範例包含正確實作的型別<xref:System.IComparable>。 程式碼註解會識別方法以滿足與相關的各種規則<xref:System.Object.Equals%2A>和<xref:System.IComparable>介面。  
  
 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式測試的行為<xref:System.IComparable>稍早所示的實作。  
  
 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)