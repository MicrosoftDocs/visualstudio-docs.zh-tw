---
title: 'CA2233: Operations should not overflow | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
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
ms.openlocfilehash: f77e3f267d991f4bffbb18c1f69f66c4603d104c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Operations should not overflow
|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A method performs an arithmetic operation and does not validate the operands beforehand to prevent overflow.  
  
## <a name="rule-description"></a>Rule Description  
 Arithmetic operations should not be performed without first validating the operands to make sure that the result of the operation is not outside the range of possible values for the data types involved. Depending on the execution context and the data types involved, arithmetic overflow can result in either a <xref:System.OverflowException?displayProperty=fullName> or the most significant bits of the result discarded.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, validate the operands before you perform the operation.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule if the possible values of the operands will never cause the arithmetic operation to overflow.  
  
## <a name="example-of-a-violation"></a>Example of a Violation  
  
### <a name="description"></a>Description  
 A method in the following example manipulates an integer that violates this rule. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requires the **Remove** integer overflow option to be disabled for this to fire.  
  
### <a name="code"></a>Code  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)] [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>Comments  
 If the method in this example is passed <xref:System.Int32.MinValue?displayProperty=fullName>, the operation would underflow. This causes the most significant bit of the result to be discarded. The following code shows how this occurs.  
  
 [C#]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 [VB]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### <a name="output"></a>Output  
  
```  
2147483647  
```  
  
## <a name="fix-with-input-parameter-validation"></a>Fix with Input Parameter Validation  
  
### <a name="description"></a>Description  
 The following example fixes the previous violation by validating the value of input.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)] [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>Fix with a Checked Block  
  
### <a name="description"></a>Description  
 The following example fixes the previous violation by wrapping the operation in a checked block. If the operation causes an overflow, a <xref:System.OverflowException?displayProperty=fullName> will be thrown.  
  
 Note that checked blocks are not supported in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Turn on Checked Arithmetic Overflow/Underflow  
 If you turn on checked arithmetic overflow/underflow in C#, it is equivalent to wrapping every integer operation in a checked block.  
  
 **To turn on checked arithmetic overflow/underflow in C#**  
  
1.  In **Solution Explorer**, right-click your project and choose **Properties**.  
  
2.  Select the **Build** tab and click **Advanced**.  
  
3.  Select **Check for arithmetic overflow/underflow** and click **OK**.  
  
## <a name="see-also"></a>See Also  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C# Operators](/dotnet/csharp/language-reference/operators/index)   
 [Checked and Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)
