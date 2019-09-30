---
title: CA2117:APTCA 類型應該只擴充 APTCA 基底類型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 832d2c9fc1d4b9138a7cd1bc39868b3c4bf1b814
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232647"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117:APTCA 類型應該只擴充 APTCA 基底類型

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因

具有<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>屬性之元件中的公用或受保護型別繼承自元件中宣告的型別，但該類型沒有屬性。

## <a name="rule-description"></a>規則描述

根據預設，具有強式名稱之元件中的公用或受保護型別會以完全信任的[InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand)隱含地受到保護。 以<xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性標記的強式名稱元件沒有此保護。 屬性會停用繼承要求。 不具有繼承需求之元件中宣告的公開類型，可由沒有完全信任的類型繼承。

當 APTCA 屬性出現在完全信任的元件上，且元件中的類型繼承自不允許部分信任呼叫端的類型時，可能會發生安全性攻擊。 如果兩種`T1`類型`T2`都符合下列條件，惡意呼叫端可以使用類型`T1`來略過保護`T2`的隱含完全信任繼承要求：

- `T1`是在具有 APTCA 屬性的完全信任元件中宣告的公用類型。

- `T1`繼承自其元件`T2`外部的類型。

- `T2`的元件沒有 APTCA 屬性，因此不應該由部分信任元件中的類型繼承。

部分信任的類型`X`可以繼承自`T1`，讓它能夠存取中`T2`所宣告的繼承成員。 因為`T2`沒有 APTCA 屬性，所以其直屬衍生型別（`T1`）必須滿足完全信任的繼承要求;`T1`具有完全信任，因此可滿足這種檢查。 安全性風險是因為`X`不會參與滿足不受信任子類別化保護`T2`的繼承要求。 基於這個理由，具有 APTCA 屬性的類型不能擴充沒有屬性的類型。

另一個安全性問題（可能是更常見的一項）是，衍生的`T1`型別（）可以透過程式設計人員錯誤，從需要完全`T2`信任的型別（）公開受保護的成員。 當此風險發生時，不受信任的呼叫端會取得僅供完全信任類型使用之資訊的存取權。

## <a name="how-to-fix-violations"></a>如何修正違規

如果違規所報告的型別是在不需要 APTCA 屬性的元件中，請將它移除。

如果需要 APTCA 屬性，請將完全信任的繼承要求加入至類型。 繼承需求可防止不受信任類型的繼承。

藉由將 APTCA 屬性加入違規所報告之基底類型的元件中，可以修正違規。 不需要先對元件中的所有程式碼進行大量的安全性審查，以及相依于元件的所有程式碼，就不要執行此動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

若要安全地隱藏這項規則的警告，您必須確保您的類型所公開的受保護成員不會直接或間接允許未受信任的呼叫者存取可以破壞性方式使用的機密資訊、作業或資源。

## <a name="example"></a>範例

下列範例會使用兩個元件和一個測試應用程式來說明此規則偵測到的安全性弱點。 第一個元件沒有 APTCA 屬性，而且不應該由部分信任的類型（ `T2`在先前的討論中表示）繼承。

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

在先前討論`T1`中所表示的第二個元件是完全受信任，並允許部分信任的呼叫端。

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

先前討論中所表示`X`的測試類型是在部分信任的元件中。

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

這個範例會產生下列輸出：

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>相關規則

[CA2116APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [從部分受信任程式碼使用程式庫](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
