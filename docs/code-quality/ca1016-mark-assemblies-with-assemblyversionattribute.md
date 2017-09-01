---
title: 'CA1016: Mark assemblies with AssemblyVersionAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
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
ms.openlocfilehash: d86a1bc4c8cbb7f327b837c03e826039f6e52e91
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Mark assemblies with AssemblyVersionAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Category|Microsoft.Design|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 The assembly does not have a version number.  
  
## <a name="rule-description"></a>Rule Description  
 The identity of an assembly is composed of the following information:  
  
-   Assembly name  
  
-   Version number  
  
-   Culture  
  
-   Public key (for strongly named assemblies).  
  
 The [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] uses the version number to uniquely identify an assembly, and to bind to types in strongly named assemblies. The version number is used together with version and publisher policy. By default, applications run only with the assembly version with which they were built.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, add a version number to the assembly by using the <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attribute. See the following example.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule for assemblies that are used by third parties, or in a production environment.  
  
## <a name="example"></a>Example  
 The following example shows an assembly that has the <xref:System.Reflection.AssemblyVersionAttribute> attribute applied.  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)] [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)] [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>See Also  
 [Assembly Versioning](/dotnet/framework/app-domains/assembly-versioning)   
 [How to: Create a Publisher Policy](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)
