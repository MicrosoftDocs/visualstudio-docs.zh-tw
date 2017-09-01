---
title: 'CA1304: Specify CultureInfo | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: aacdab5f70f27a110414270d8584ce3ca97f47aa
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Specify CultureInfo
|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|CheckId|CA1304|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A method or constructor calls a member that has an overload that accepts a <xref:System.Globalization.CultureInfo?displayProperty=fullName> parameter, and the method or constructor does not call the overload that takes the <xref:System.Globalization.CultureInfo> parameter. This rule ignores calls to the following methods:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Rule Description  
 When a <xref:System.Globalization.CultureInfo> or <xref:System.IFormatProvider?displayProperty=fullName> object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales. Also, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] members choose default culture and formatting based on assumptions that might not be correct for your code. To ensure the code works as expected for your scenarios, you should supply culture-specific information according to the following guidelines:  
  
-   If the value will be displayed to the user, use the current culture. See <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   If the value will be stored and accessed by software, that is, persisted to a file or database, use the invariant culture. See <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   If you do not know the destination of the value, have the data consumer or provider specify the culture.  
  
 Note that <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> is used only to retrieve localized resources by using an instance of the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.  
  
 Even if the default behavior of the overloaded member is appropriate for your needs, it is better to explicitly call the culture-specific overload so that your code is self-documenting and more easily maintained.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, use the overload that takes a <xref:System.Globalization.CultureInfo> or <xref:System.IFormatProvider> and specify the argument according to the guidelines that were listed earlier.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule when it is certain that the default culture/format provider is the correct choice, and where code maintainability is not an important development priority.  
  
## <a name="example"></a>Example  
 In the following example, `BadMethod` causes two violations of this rule. `GoodMethod` corrects the first violation by passing the invariant culture to System.String.Compare, and corrects the second violation by passing the current culture to <xref:System.String.ToLower%2A> because `string3` is displayed to the user.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## <a name="example"></a>Example  
 The following example shows the effect of current culture on the default <xref:System.IFormatProvider> that is selected by the <xref:System.DateTime> type.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 This example produces the following output.  
  
 **6/4/1900 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Related Rules  
 [CA1305: Specify IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## <a name="see-also"></a>See Also  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/en-us/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
