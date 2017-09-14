---
title: 'CA1901: P-Invoke declarations should be portable | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
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
ms.openlocfilehash: fb3ea2ab50f10dcb348c03a716c1eba5bee7e630
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: P/Invoke declarations should be portable
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Category|Microsoft.Portability|  
|Breaking Change|Breaking - If the P/Invoke is visible outside the assembly. Non Breaking - If the P/Invoke is not visible outside the assembly.|  
  
## <a name="cause"></a>Cause  
 This rule evaluates the size of each parameter and the return value of a P/Invoke and verifies that their size, when marshaled to unmanaged code on 32-bit and 64-bit platforms, is correct. The most common violation of this rule is to pass a fixed-sized integer where a platform-dependent, pointer-sized variable is required.  
  
## <a name="rule-description"></a>Rule Description  
 Either of the following scenarios violates this rule occurs:  
  
-   The return value or parameter is typed as a fixed-size integer when it should be typed as an `IntPtr`.  
  
-   The return value or parameter is typed as an `IntPtr` when it should be typed as a fixed-size integer.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 You can fix this violation by using `IntPtr` or `UIntPtr` to represent handles instead of `Int32` or `UInt32`.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 You should not suppress this warning.  
  
## <a name="example"></a>Example  
 The following example demonstrates a violation of this rule.  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 In this example, the `nIconIndex` parameter is declared as an `IntPtr`, which is 4 bytes wide on a 32-bit platform and 8 bytes wide on a 64-bit platform. In the unmanaged declaration that follows, you can see that `nIconIndex` is a 4-byte unsigned integer on all platforms.  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>Example  
 To fix the violation, change the declaration to the following:  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>See Also  
 [Portability Warnings](../code-quality/portability-warnings.md)
