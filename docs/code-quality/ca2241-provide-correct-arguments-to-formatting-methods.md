---
title: 'CA2241: Provide correct arguments to formatting methods | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
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
ms.openlocfilehash: 4ed5e5210683f073abcc65943fc7ae01677bf775
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Provide correct arguments to formatting methods
|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 The `format` string argument passed to a method such as <xref:System.Console.WriteLine%2A>,  <xref:System.Console.Write%2A>, or  <xref:System.String.Format%2A?displayProperty=fullName> does not contain a format item that corresponds to each object argument, or vice versa.  
  
## <a name="rule-description"></a>Rule Description  
 The arguments to methods such as <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, and <xref:System.String.Format%2A> consist of a format string followed by several <xref:System.Object?displayProperty=fullName> instances. The format string consists of text and embedded format items of the form, {index[,alignment][:formatString]}. 'index' is a zero-based integer that indicates which of the objects to format. If an object does not have a corresponding index in the format string, the object is ignored. If the object specified by 'index' does not exist, a <xref:System.FormatException?displayProperty=fullName> is thrown at runtime.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, provide a format item for each object argument and provide an object argument for each format item.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example shows two violations of the rule.  
  
 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)] [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]
