---
title: CA2116：APTCA 方法應該只呼叫 APTCA 方法
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 300b08d6fd00a9bf2a38e738a3b4d433111cb8c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116：APTCA 方法應該只呼叫 APTCA 方法
|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 中的組件的方法<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>屬性沒有屬性的組件中呼叫的方法。

## <a name="rule-description"></a>規則描述
 根據預設，公用或受保護的方法，以強式名稱組件中會以隱含方式受到[連結要求](/dotnet/framework/misc/link-demands)完全信任。 只有完全受信任的呼叫端可以存取的強式名稱組件。 強式名稱組件標示<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性並沒有這項保護。 屬性會停用連結需求，讓呼叫端沒有完全信任，例如從近端內部網路或網際網路執行的程式碼可以存取組件。

 當 APTCA 屬性完全受信任的組件，並且組件中不允許部分信任呼叫端的另一個組件中執行程式碼時，就可以 安全性弱點攻擊。 如果兩個方法`M1`和`M2`符合下列條件，惡意呼叫端可以使用此方法`M1`略過隱含完全信任的連結要求保護`M2`:

-   `M1` 具有 APTCA 屬性的完全信任組件中宣告的公用方法。

-   `M1` 呼叫的方法`M2`外`M1`的組件。

-   `M2`組件沒有 APTCA 屬性，因此，不應執行的身分或代表部分信任的呼叫端。

 部分信任呼叫端`X`可以呼叫方法`M1`，因而導致`M1`呼叫`M2`。 因為`M2`沒有 APTCA 屬性，其立即呼叫端 (`M1`) 必須滿足連結要求完全信任。`M1`具有完全信任，因此會滿足這項檢查。 安全性風險是因為`X`不會參與滿足連結要求保護`M2`來自不受信任的呼叫端。 因此，使用 APTCA 屬性的方法不可以呼叫不具有屬性的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果需要 APCTA 屬性，使用需求來保護完全信任組件呼叫的方法。 您的需求將取決於您的方法所公開的功能完全權限。 如果可能的話，保護具有完全信任，以確保基礎功能，不會公開給部分信任呼叫端要求的方法。 如果不可行，請選取一組權限可有效保護公開的功能。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定，您的方法所公開的功能不會直接或間接允許來電者存取機密資訊、 作業或資源，可用於破壞性的方式。

## <a name="example"></a>範例
 下列範例會使用兩個組件和測試應用程式，說明這個規則偵測到的安全性弱點。 第一個組件並沒有 APTCA 屬性，而不應存取部分信任呼叫端 (由`M2`在先前的討論內容)。

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example"></a>範例
 第二個組件是完全受信任，並允許部分信任呼叫端 (由`M1`在先前的討論內容)。

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example"></a>範例
 測試應用程式 (由`X`在先前的討論內容) 受到部分信任。

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

 此範例會產生下列輸出。

 **要求完全信任： 要求失敗。** 
 **ClassRequiringFullTrust.DoWork 呼叫。**
## <a name="related-rules"></a>相關的規則
 [CA2117：APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>另請參閱
 [安全編碼方針](/dotnet/standard/security/secure-coding-guidelines)[使用程式庫，從部分信任的程式碼](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)[連結要求](/dotnet/framework/misc/link-demands)[資料與模型化](/dotnet/framework/data/index)