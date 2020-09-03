---
title: CA2102：攔截一般處理常式中的非 CLSCompliant 例外狀況 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521299"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102:必須使用一般處理常式攔截非 CLSCompliant 例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 元件中未標示或的成員會被標記為 <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> `RuntimeCompatibility(WrapNonExceptionThrows = false)` 包含處理 <xref:System.Exception?displayProperty=fullName> 且不包含緊接在一般 catch 區塊後面的 catch 區塊。 此規則會忽略 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 元件。

## <a name="rule-description"></a>規則描述
 處理的 catch 區塊會攔截 <xref:System.Exception> 所有 Common Language Specification (符合 cls) 規範的例外狀況。 不過，它不會攔截不符合 CLS 規範的例外狀況。 不符合 CLS 標準的例外狀況可以從機器碼或由 Microsoft 中繼語言 (MSIL) 組合語言產生的 managed 程式碼擲回。 請注意，c # 和 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 編譯器不允許擲回不符合 cls 規範的例外狀況，也不 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 會攔截不符合 cls 規範的例外狀況。 如果 catch 區塊的目的是要處理所有例外狀況，請使用下列一般 catch 區塊語法。

- C#: `catch {}`

- C + +： `catch(...) {}` 或 `catch(Object^) {}`

  在 catch 區塊中移除先前允許的許可權時，未處理的不符合 CLS 標準例外狀況會成為安全性問題。 因為不會攔截到不符合 CLS 規範的例外狀況，所以會以較高的許可權來執行擲回不符合 CLS 標準之例外狀況的惡意方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要在意圖要攔截所有例外狀況時修正此規則的違規情形，請替代或加入一般 catch 區塊或標記元件 `RuntimeCompatibility(WrapNonExceptionThrows = true)` 。 如果在 catch 區塊中移除許可權，請複製一般 catch 區塊中的功能。 如果它不是處理所有例外狀況的意圖，請 <xref:System.Exception> 使用處理特定例外狀況類型的 catch 區塊來取代處理的 catch 區塊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果 try 區塊未包含任何可能會產生不符合 CLS 規範之例外狀況的語句，則可以安全地隱藏此規則的警告。 因為任何原生或 managed 程式碼可能會擲回不符合 CLS 規範的例外狀況，所以需要知道可在 try 區塊內的所有程式碼路徑中執行的所有程式碼。 請注意，通用語言執行時間不會擲回不符合 CLS 規範的例外狀況。

## <a name="example"></a>範例
 下列範例顯示的 MSIL 類別會擲回不符合 CLS 規範的例外狀況。

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
 下列範例顯示的方法包含符合規則的一般 catch 區塊。

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 編譯先前的範例，如下所示。

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>相關規則
 [CA1031:不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>另請參閱
 [例外狀況和例外狀況處理](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (IL](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f)組合器) 覆[寫安全性檢查](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28)[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
