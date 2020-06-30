---
title: CA2116： APTCA 方法應該只呼叫 APTCA 方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 115c0e733716994ba463eada938f8ff908612d0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547754"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116:APTCA 方法應該只呼叫 APTCA 方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件中具有屬性的方法， <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 會呼叫元件中沒有該屬性的方法。

## <a name="rule-description"></a>規則描述
 根據預設，具有強式名稱之元件中的公用或受保護方法，會以完全信任的[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)來隱含保護;只有完全受信任的呼叫端可以存取強式名稱的元件。 以（APTCA）屬性標記的強式名稱元件沒有 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 此保護。 屬性會停用連結要求，讓不具有完全信任的呼叫端可以存取元件，例如從內部網路或網際網路執行的程式碼。

 當完全信任的元件上出現 APTCA 屬性，而且元件在不允許部分信任呼叫端的另一個元件中執行程式碼時，可能會有安全性攻擊。 如果兩種 `M1` 方法 `M2` 都符合下列條件，惡意的呼叫者就可以使用方法， `M1` 略過保護的隱含完全信任連結要求 `M2` ：

- `M1`是在具有 APTCA 屬性的完全信任元件中宣告的公用方法。

- `M1`呼叫 `M2` 元件外部的方法 `M1` 。

- `M2`的元件沒有 APTCA 屬性，因此不應該由或代表部分信任的呼叫端來執行。

  部分信任的呼叫端 `X` 可以呼叫方法 `M1` ，因而導致 `M1` 呼叫 `M2` 。 因為沒有 `M2` APTCA 屬性，所以其立即呼叫端（ `M1` ）必須滿足完全信任的連結要求; `M1` 具有完全信任，因此可滿足這種檢查。 安全性風險是因為不 `X` 會參與滿足不受信任呼叫者保護的連結要求 `M2` 。 因此，具有 APTCA 屬性的方法不能呼叫沒有屬性的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果需要 APCTA 屬性，請使用要求來保護呼叫完全信任元件的方法。 您所要求的確切許可權將取決於您的方法所公開的功能。 如果可行，請以完全信任的需求來保護方法，以確保基礎功能不會公開給部分信任的呼叫端。 如果無法這麼做，請選取一組可有效保護已公開功能的許可權。 如需有關需求的詳細資訊，請參閱[要求](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏這項規則的警告，您必須確定方法所公開的功能不會直接或間接允許呼叫端存取機密資訊、作業，或可利用破壞性方式使用的資源。

## <a name="example"></a>範例
 下列範例會使用兩個元件和一個測試應用程式來說明此規則偵測到的安全性弱點。 第一個元件沒有 APTCA 屬性，而且不應該存取部分信任的呼叫端（ `M2` 在先前的討論中表示）。

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>範例
 第二個元件是完全受信任，並允許部分信任的呼叫端（ `M1` 在先前的討論中表示）。

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>範例
 測試應用程式（ `X` 在先前的討論中表示）是部分信任的。

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 此範例會產生下列輸出。

 **完全信任的要求：要求失敗。** 
**已呼叫 ClassRequiringFullTrust. DoWork。**
## <a name="related-rules"></a>相關規則
 [CA2117:APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>另請參閱
 安全程式碼撰寫[指導方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework 元件可由部分信任程式碼](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d)[使用程式庫，從部分信任的程式碼](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)[要求](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)、[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
