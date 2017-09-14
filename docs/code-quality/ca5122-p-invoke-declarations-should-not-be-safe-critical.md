---
title: CA5122 P-Invoke declarations should not be safe critical | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a180aaeb955660ce0eb8d9e317ae8babc598a8a5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 P/Invoke declarations should not be safe critical
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A P/Invoke declaration has been marked with a <xref:System.Security.SecuritySafeCriticalAttribute>:  
  
```csharp  
[assembly: AllowPartiallyTrustedCallers]  
  
// ...  
public class C  
{  
    [SecuritySafeCritical]  
    [DllImport("kernel32.dll")]  
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke  
   }  
  
```  
  
 In this example, `C.Beep(...)` has been marked as a security safe critical method.  
  
## <a name="rule-description"></a>Rule Description  
 Methods are marked as SecuritySafeCritical when they perform a security sensitive operation, but are also safe to be used by transparent code. One of the fundamental rules of the security transparency model is that transparent code may never directly call native code through a P/Invoke. Therefore, marking a P/Invoke as security safe critical will not enable transparent code to call it, and is misleading for security analysis.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To make a P/Invoke available to transparent code, expose a security safe critical wrapper method for it:  
  
```csharp  
[assembly: AllowPartiallyTrustedCallers  
  
class C  
{  
   [SecurityCritical]  
   [DllImport("kernel32.dll", EntryPoint="Beep")]  
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke  
  
   [SecuritySafeCritical]  
   public static bool Beep(int frequency, int duration)  
   {  
      return BeepPInvoke(frequency, duration);  
   }  
}  
  
```  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.
