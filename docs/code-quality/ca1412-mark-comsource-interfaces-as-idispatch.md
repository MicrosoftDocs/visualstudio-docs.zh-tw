---
title: 'CA1412: Mark ComSource Interfaces as IDispatch | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
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
ms.openlocfilehash: 0a12e8ed8b7ef2d64c53837eca32f3823fc421d3
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Mark ComSource Interfaces as IDispatch
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A type is marked with the <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribute and at least one specified interface is not marked with the <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribute set to the `InterfaceIsDispatch` value.  
  
## <a name="rule-description"></a>Rule Description  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> is used to identify the event interfaces that a class exposes to Component Object Model (COM) clients. These interfaces must be exposed as `InterfaceIsIDispatch` to enable Visual Basic 6 COM clients to receive event notifications. By default, if an interface is not marked with the <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribute, it is exposed as a dual interface.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, add or modify the <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribute so that its value is set to InterfaceIsIDispatch for all interfaces that are specified with the <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribute.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example shows a class where one of the interfaces violates the rule.  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)] [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1408: Do not use AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>See Also  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index)
