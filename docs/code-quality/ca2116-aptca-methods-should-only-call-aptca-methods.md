---
title: CA2116:APTCA 方法應該只呼叫 APTCA 方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03c00efe53a5385d7604d0191ff60ae70888e655
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954431"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116:APTCA 方法應該只呼叫 APTCA 方法

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因

組件中的方法<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>屬性並沒有屬性的組件中呼叫的方法。

## <a name="rule-description"></a>規則描述

根據預設，公用或受保護的方法，以強式名稱的組件中會以隱含方式受到[連結要求](/dotnet/framework/misc/link-demands)完全信任。 只有完全受信任呼叫端可以存取的強式名稱組件。 強式名稱組件標示<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性並沒有這項保護。 屬性會停用連結需求，讓呼叫端沒有完全信任，例如從近端內部網路或網際網路執行的程式碼可以存取組件。

當 APTCA 屬性存在於上是完全受信任的組件，組件不允許部分信任呼叫端的另一個組件中執行程式碼，就可以 產生安全性弱點。 如果兩個方法`M1`並`M2`符合下列條件，惡意呼叫端可以使用此方法`M1`略過隱含的完全信任的連結要求保護`M2`:

- `M1` 具有 APTCA 屬性的完全信任組件中宣告的公用方法。

- `M1` 呼叫方法`M2`外部`M1`的組件。

- `M2`組件不具有 APTCA 屬性，因此，不應執行或代表，都是部分信任呼叫端。

部分信任呼叫端`X`可以呼叫方法`M1`，而導致`M1`呼叫`M2`。 因為`M2`APTCA 屬性，其立即呼叫端沒有 (`M1`) 必須滿足連結要求完全信任。`M1`具有完全信任，因此滿足這項檢查。 安全性風險是，因為`X`不會參與滿足連結要求保護`M2`來自不受信任的呼叫者。 因此，若方法具有 APTCA 屬性必須呼叫不具有屬性的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果需要 APCTA 屬性，使用需求來保護在完全信任組件呼叫的方法。 您的需求將取決於您的方法所公開的功能完全權限。 如果可能，保護以確保不會對部分信任呼叫端公開的基礎功能的完全信任要求的方法。 如果這不可行，請選取一組權限可有效保護公開的功能。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定，您的方法所公開的功能不會直接或間接允許來電者存取機密資訊、 作業或可以用於破壞性方式的資源。

## <a name="example-1"></a>範例 1
 下列範例會使用兩個組件和測試應用程式，說明這個規則偵測到的安全性弱點。 第一個組件並沒有 APTCA 屬性，而且應該無法存取部分信任呼叫端 (由`M2`中先前的討論)。

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>範例 2
 第二個組件是完全受信任，並允許部分信任呼叫端 (由`M1`中先前的討論)。

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>範例 3
 測試應用程式 (由`X`中先前的討論) 是以部分信任。

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

這個範例會產生下列輸出：

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>相關的規則

- [CA2117:APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [從部分受信任程式碼使用程式庫](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [連結要求](/dotnet/framework/misc/link-demands)
- [資料與模型化](/dotnet/framework/data/index)