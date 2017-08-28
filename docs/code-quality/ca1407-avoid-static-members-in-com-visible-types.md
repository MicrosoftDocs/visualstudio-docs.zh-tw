---
title: 'CA1407: Avoid static members in COM visible types | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 23
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 773b2a47914aa31865220ae0402b61ad78d67f4a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Avoid static members in COM visible types
|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A type that is specifically marked as visible to Component Object Model (COM) contains a `public``static` method.  
  
## <a name="rule-description"></a>Rule Description  
 COM does not support `static` methods.  
  
 This rule ignores property and event accessors, operator overloading methods, or methods that are marked by using either the <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribute or the <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribute.  
  
 By default, the following are visible to COM: assemblies, public types, public instance members in public types, and all members of public value types.  
  
 For this rule to occur, an assembly-level <xref:System.Runtime.InteropServices.ComVisibleAttribute> must be set to `false` and the class- <xref:System.Runtime.InteropServices.ComVisibleAttribute> must be set to `true`, as the following code shows.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, change the design to use an instance method that provides the same functionality as the `static` method.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule if a COM client does not require access to the functionality that is provided by the `static` method.  
  
## <a name="example-violation"></a>Example Violation  
  
### <a name="description"></a>Description  
 The following example shows a `static` method that violates this rule.  
  
### <a name="code"></a>Code  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>Comments  
 In this example, the **Book.FromPages** method cannot be called from COM.  
  
## <a name="example-fix"></a>Example Fix  
  
### <a name="description"></a>Description  
 To fix the violation in the previous example, you could change the method to an instance method, but that does not make sense in this instance. A better solution is to explicitly apply `ComVisible(false)` to the method to make it clear to other developers that the method cannot be seen from COM.  
  
 The following example applies <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> to the method.  
  
### <a name="code"></a>Code  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1017: Mark assemblies with ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Avoid Int64 arguments for Visual Basic 6 clients](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Avoid non-public fields in COM visible value types](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>See Also  
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index)
