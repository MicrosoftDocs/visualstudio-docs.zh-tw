---
title: CA2111：指標不應該為可見的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7429251a66ce2fe22a825a153cb90248faabb9fd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544361"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111:指標不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的 <xref:System.IntPtr?displayProperty=fullName> 或 <xref:System.UIntPtr?displayProperty=fullName> 欄位不是唯讀的。

## <a name="rule-description"></a>規則描述
 <xref:System.IntPtr>和 <xref:System.UIntPtr> 是用來存取非受控記憶體的指標類型。 如果指標不是私用、內部或唯讀，惡意程式碼可能會變更指標的值，可能會允許存取記憶體中的任意位置，或是造成應用程式或系統失敗。

 如果您想要保護包含指標欄位之類型的存取權，請參閱[CA2112：受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 藉由將指標設為唯讀、內部或私用來保護其安全。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不依賴指標的值，請隱藏此規則的警告。

## <a name="example"></a>範例
 下列程式碼顯示違反並滿足規則的指標。 請注意，非私用指標也違反規則[CA1051：不要宣告可見的實例欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2112:受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051:不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>另請參閱
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
