---
title: CA2117:APTCA 類型應該只擴充 APTCA 基底類型
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc2086038187093397d53e80b1a26f2006c32c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873349"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117:APTCA 類型應該只擴充 APTCA 基底類型

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因

公用或受保護的類型與組件中<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>屬性繼承自沒有屬性的組件中宣告的型別。

## <a name="rule-description"></a>規則描述

根據預設，使用強式名稱的組件中的公用或受保護的類型隱含地受到[InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand)完全信任。 強式名稱組件標示<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性並沒有這項保護。 屬性會停用繼承要求。 公開沒有繼承要求的組件中宣告的型別會繼承並未受完全信任的類型。

APTCA 屬性存在於上是完全受信任的組件，組件中的型別繼承自不允許部分信任呼叫端的類型，產生安全性弱點時，可能。 如果兩種型別`T1`並`T2`符合下列條件，惡意呼叫端可以使用型別`T1`略過隱含的完全信任的繼承要求保護`T2`:

- `T1` 具有 APTCA 屬性的完全信任組件中宣告的公用型別。

- `T1` 繼承自型別`T2`組件外部。

- `T2`組件不具有 APTCA 屬性，因此，應該不會繼承由部分信任的組件中的型別。

部分信任的型別`X`可以繼承自`T1`，讓它存取中宣告的繼承成員`T2`。 因為`T2`沒有 APTCA 屬性，其直屬的衍生型別 (`T1`) 必須符合繼承要求完全信任。`T1`具有完全信任，因此滿足這項檢查。 安全性風險是，因為`X`不會參與滿足繼承要求保護`T2`來自不受信任的子類別化。 基於這個理由，具有 APTCA 屬性的型別必須延伸不具有屬性的類型。

另一個安全性問題，並可能是較常見的其中一個，是衍生型別 (`T1`) 可以透過程式設計錯誤，公開受保護的成員，從需要完全信任的型別 (`T2`)。 此公開資訊時，不受信任的呼叫端就會獲得存取權應該僅適用於完全信任類型的資訊。

## <a name="how-to-fix-violations"></a>如何修正違規

如果違規所報告的類型位於組件，而無須 APTCA 屬性，請將它移除。

如果需要 APTCA 屬性，加入類型繼承要求完全信任。 繼承要求可防止未受信任的型別所繼承。

可以藉由將 APTCA 屬性新增至基底類型的違規所回報的組件中修正的違規情形。 請不要這樣不含第一個執行的組件中的所有程式碼和所有相依於組件的程式碼需要大量的安全性檢閱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

若要安全地隱藏此規則的警告，您必須確定，您的型別所公開的受保護的成員不直接或間接允許不受信任的來電者存取機密資訊、 作業或可以用於破壞性方式的資源。

## <a name="example"></a>範例

下列範例會使用兩個組件和測試應用程式，說明這個規則偵測到的安全性弱點。 第一個組件並沒有 APTCA 屬性，而且不能由部分信任的型別可繼承 (由`T2`中先前的討論)。

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

第二個組件，由`T1`在先前的討論中，是完全受信任，並允許部分信任呼叫端。

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

測試類型，由`X`在先前的討論中，是在部分信任的組件中。

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

這個範例會產生下列輸出：

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>相關的規則

[CA2116:APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [從部分受信任程式碼使用程式庫](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
