---
title: CA2111:指標不應該為可見的
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 416e45337dafd11a00e98b9adda9f16b02139f9c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921659"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111:指標不應該為可見的

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
公用或受保護<xref:System.IntPtr?displayProperty=fullName>的<xref:System.UIntPtr?displayProperty=fullName>或欄位不是唯讀的。

## <a name="rule-description"></a>規則描述
 <xref:System.IntPtr>和<xref:System.UIntPtr>是用來存取非受控記憶體的指標類型。 如果指標不是私用、內部或唯讀, 惡意程式碼可能會變更指標的值, 可能會允許存取記憶體中的任意位置, 或是造成應用程式或系統失敗。

如果您想要保護包含指標欄位之類型的存取權, 請參閱[CA2112:受保護的類型不應該](../code-quality/ca2112-secured-types-should-not-expose-fields.md)公開欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
藉由將指標設為唯讀、內部或私用來保護其安全。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果您不依賴指標的值, 請隱藏此規則的警告。

## <a name="example"></a>範例
下列程式碼顯示違反並滿足規則的指標。 請注意, 非私用指標也違反規則[CA1051:不要宣告可見的實例欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>相關規則
[CA2112受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051不要宣告可見的實例欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>另請參閱

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>