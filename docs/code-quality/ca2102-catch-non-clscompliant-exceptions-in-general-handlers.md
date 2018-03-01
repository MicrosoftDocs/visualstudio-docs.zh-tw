---
title: "CA2102： 在一般處理常式中攔截非 CLSCompliant 的例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 17238e140f8672e9d2d5a67594eb26b415c0b8d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102：在一般處理常式中攔截非 CLSCompliant 的例外狀況
|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|分類|Microsoft.Security|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 未標示為組件中的成員<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute>或標示`RuntimeCompatibility(WrapNonExceptionThrows = false)`包含處理的 catch 區塊<xref:System.Exception?displayProperty=fullName>，而且不包含緊接其後的一般 catch 區塊。 此規則會忽略[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]組件。  
  
## <a name="rule-description"></a>規則描述  
 處理的 catch 區塊<xref:System.Exception>攔截所有 Common Language Specification (CLS) 標準的例外狀況。 不過，它不會攔截不符合 CLS 標準的例外狀況。 不符合 CLS 標準的例外狀況擲回從原生程式碼或 managed 程式碼所產生的 Microsoft 中繼語言 (MSIL) 組譯工具。 請注意，C# 和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編譯器不允許不符合 CLS 標準的例外狀況擲回和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]不會攔截不符合 CLS 標準的例外狀況。 如果 catch 區塊的目的是要處理所有例外狀況，請使用下列的一般 catch 區塊語法。  
  
-   C#: `catch {}`  
  
-   C + +:`catch(...) {}`或`catch(Object^) {}`  
  
 在 catch 區塊中移除先前允許的使用權限時，未處理不符合 CLS 標準的例外狀況就會成為安全性問題。 由於不符合 CLS 標準的例外狀況並不會遭到攔截，惡意的方法會擲回不符合 CLS 標準的例外狀況無法執行提高權限。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，當目的是要攔截所有例外狀況，以取代或新增的一般 catch 區塊或標示組件`RuntimeCompatibility(WrapNonExceptionThrows = true)`。 如果在 catch 區塊中移除的權限，重複的功能的一般 catch 區塊。 如果不是其用意是為了處理所有例外狀況，取代處理 catch 區塊<xref:System.Exception>處理特定的例外狀況類型的 catch 區塊。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果在 try 區塊沒有包含任何可能會產生不符合 CLS 標準的例外狀況的陳述式。 任何原生或 managed 程式碼可能會擲回不符合 CLS 標準的例外狀況，因為這需要的所有程式碼可以在 try 區塊內的所有程式碼路徑中執行的知識。 請注意，由 common language runtime 不擲回不符合 CLS 標準的例外狀況。  
  
## <a name="example"></a>範例  
 下列範例會擲回不符合 CLS 標準的例外狀況的 MSIL 類別。  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>範例  
 下列範例顯示包含符合規則的一般 catch 區塊的方法。  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 編譯先前的範例如下所示。  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>相關的規則  
 [CA1031：不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>請參閱  
 [例外狀況和例外狀況處理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe (IL 組譯工具)](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)