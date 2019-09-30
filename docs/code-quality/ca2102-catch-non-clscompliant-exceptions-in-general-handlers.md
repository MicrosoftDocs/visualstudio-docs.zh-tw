---
title: CA2102:必須使用一般處理常式攔截非 CLSCompliant 例外狀況
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233003"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102:必須使用一般處理常式攔截非 CLSCompliant 例外狀況

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|分類|Microsoft.Security|
|重大變更|不中斷|

## <a name="cause"></a>原因

元件中未標記<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute>為或的成員會標示`RuntimeCompatibility(WrapNonExceptionThrows = false)`為包含處理<xref:System.Exception?displayProperty=fullName>且不包含緊接在一般 catch 區塊後面的 catch 區塊。 此規則會[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]忽略元件。

## <a name="rule-description"></a>規則描述

處理<xref:System.Exception>捕捉所有 Common Language Specification （CLS）相容例外狀況的 catch 區塊。 不過，它不會攔截不符合 CLS 規範的例外狀況。 不符合 CLS 規範的例外狀況可以從機器碼或由 Microsoft 中繼語言（MSIL）組合器所產生的 managed 程式碼擲回。 請注意， C#和[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編譯器不允許擲回不符合 cls 規範的例外狀況， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]而且不會攔截不符合 cls 規範的例外狀況。 如果 catch 區塊的目的是要處理所有例外狀況，請使用下列一般 catch 區塊語法。

- C#: `catch {}`

- C++： `catch(...) {}`或`catch(Object^) {}`

在 catch 區塊中移除先前允許的許可權時，未處理的不符合 CLS 規範的例外狀況會成為安全性問題。 由於不會攔截到不符合 CLS 規範的例外狀況，因此可能會以較高的許可權來執行擲回不符合 CLS 標準之例外狀況的惡意方法。

## <a name="how-to-fix-violations"></a>如何修正違規

若要在目的是要攔截所有例外狀況時修正此規則的違規，請取代或加入一般 catch 區塊或標記元件`RuntimeCompatibility(WrapNonExceptionThrows = true)`。 如果已移除 catch 區塊中的許可權，請複製一般 catch 區塊中的功能。 如果不是處理所有例外狀況的意圖，請將處理<xref:System.Exception>的 catch 區塊取代為處理特定例外狀況類型的 catch 區塊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果 try 區塊未包含任何可能產生不符合 CLS 標準之例外狀況的語句，則可以放心地隱藏此規則的警告。 因為任何原生或 managed 程式碼可能會擲回不符合 CLS 規範的例外狀況，所以這需要知道在 try 區塊內的所有程式碼路徑中可執行檔所有程式碼。 請注意，common language runtime 不會擲回不符合 CLS 規範的例外狀況。

## <a name="example-1"></a>範例 1

下列範例顯示的 MSIL 類別會擲回不符合 CLS 規範的例外狀況。

```cpp
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

下列範例顯示的方法包含符合規則的一般 catch 區塊。

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

編譯先前的範例，如下所示。

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>相關規則

[CA1031不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>另請參閱

- [例外狀況和例外狀況處理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (IL 組譯工具)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)