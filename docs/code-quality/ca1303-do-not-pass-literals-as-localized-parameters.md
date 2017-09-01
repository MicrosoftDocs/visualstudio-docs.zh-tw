---
title: 'CA1303: Do not pass literals as localized parameters | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 98989e398166e8fc5a5fc0c765b10a11a12d5083
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Do not pass literals as localized parameters
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A method passes a string literal as a parameter to a constructor or method in the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] class library and that string should be localizable.  
  
 This warning is raised when a literal string is passed as a value to a parameter or property and one or more of the following cases is true:  
  
-   The <xref:System.ComponentModel.LocalizableAttribute> attribute of the parameter or property is set to true.  
  
-   The parameter or property name contains "Text", "Message", or "Caption".  
  
-   The name of the string parameter that is passed to a Console.Write or Console.WriteLine method is either "value" or "format".  
  
## <a name="rule-description"></a>Rule Description  
 String literals that are embedded in source code are difficult to localize.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, replace the string literal with a string retrieved through an instance of the <xref:System.Resources.ResourceManager> class.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule if the code library will not be localized, or if the string is not exposed to the end user or a developer using the code library.  
  
 Users can eliminate noise against methods which should not be passed localized strings by either renaming the parameter or property named, or by marking these items as conditional.  
  
## <a name="example"></a>Example  
 The following example shows a method that throws an exception when either of its two arguments are out of range. For the first argument, the exception constructor is passed a literal string, which violates this rule. For the second argument, the constructor is correctly passed a string retrieved through a <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)] [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)] [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>See Also  
 [Resources in Desktop Apps](/dotnet/framework/resources/index)
