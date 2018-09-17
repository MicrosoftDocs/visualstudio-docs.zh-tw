---
title: CA2102：在一般處理常式中攔截非 CLSCompliant 的例外狀況
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f424ec6585119619cc7fa64efe5d436779b8a65
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547447"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102：在一般處理常式中攔截非 CLSCompliant 的例外狀況

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|類別|Microsoft.Security|
|中斷變更|非重大|

## <a name="cause"></a>原因
 未標記為組件中的成員<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute>，或已標示`RuntimeCompatibility(WrapNonExceptionThrows = false)`包含 catch 區塊處理<xref:System.Exception?displayProperty=fullName>，而且不包含緊接的一般 catch 區塊。 此規則會忽略[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]組件。

## <a name="rule-description"></a>規則描述
 Catch 區塊處理<xref:System.Exception>取得所有與 Common Language Specification (CLS) 規範的例外狀況。 不過，它不會攔截非 CLS 標準的例外狀況。 不符合 CLS 相容的例外狀況擲回的原生程式碼，或從 managed 程式碼所產生的 Microsoft intermediate language (MSIL) 組譯工具。 請注意，C# 和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編譯器不允許不符合 CLS 規範的例外狀況擲回和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]不會攔截非 CLS 標準的例外狀況。 如果 catch 區塊的目的是要處理所有例外狀況，請使用下列的一般 catch 區塊語法。

- C#: `catch {}`

- C + +:`catch(...) {}`或 `catch(Object^) {}`

 在 catch 區塊中移除先前允許的權限時，未處理的非符合 CLS 規範的例外狀況就會成為安全性問題。 因為系統不會攔截非 CLS 標準的例外狀況，擲回不符合 CLS 規範的例外狀況的惡意方法可以執行以提高權限。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，當目的是要攔截所有例外狀況，以取代或新增的一般 catch 區塊或標示組件`RuntimeCompatibility(WrapNonExceptionThrows = true)`。 如果在 catch 區塊中移除權限，重複的功能的一般 catch 區塊。 如果不打算處理所有例外狀況，取代 catch 區塊處理<xref:System.Exception>處理特定的例外狀況類型的 catch 區塊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告，如果在 try 區塊中不含任何可能會產生不符合 CLS 規範的例外狀況的陳述式。 任何原生或 managed 程式碼可能會擲回不符合 CLS 規範的例外狀況，因為這會需要的所有程式碼都可以在 try 區塊內的所有程式碼路徑中執行的知識。 請注意，由 common language runtime 不擲回不符合 CLS 標準的例外狀況。

## <a name="example-1"></a>範例 1
 下列範例示範會擲回不符合 CLS 規範的例外狀況的 MSIL 類別。

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

## <a name="example-2"></a>範例 2
 下列範例會示範包含符合規則的一般 catch 區塊的方法。

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

 編譯先前的範例如下所示。

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>相關的規則
 [CA1031：不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>另請參閱

- [例外狀況和例外狀況處理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (IL 組譯工具)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)