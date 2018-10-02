---
title: 'CA2116: APTCA 方法應該只呼叫 APTCA 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 78e3136ed2671de2962ae4de994bae178fcbceca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588313"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116：APTCA 方法應該只呼叫 APTCA 方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2116: APTCA 方法應該只呼叫 APTCA 方法](https://docs.microsoft.com/visualstudio/code-quality/ca2116-aptca-methods-should-only-call-aptca-methods)。

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 組件中的方法<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>屬性並沒有屬性的組件中呼叫的方法。

## <a name="rule-description"></a>規則描述
 根據預設，公用或受保護的方法，以強式名稱的組件中會以隱含方式受到[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)完全信任。 只有完全受信任呼叫端可以存取的強式名稱組件。 強式名稱組件標示<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性並沒有這項保護。 屬性會停用連結需求，讓呼叫端沒有完全信任，例如從近端內部網路或網際網路執行的程式碼可以存取組件。

 當 APTCA 屬性存在於上是完全受信任的組件，組件不允許部分信任呼叫端的另一個組件中執行程式碼，就可以 產生安全性弱點。 如果兩個方法`M1`並`M2`符合下列條件，惡意呼叫端可以使用此方法`M1`略過隱含的完全信任的連結要求保護`M2`:

-   `M1` 具有 APTCA 屬性的完全信任組件中宣告的公用方法。

-   `M1` 呼叫方法`M2`外部`M1`的組件。

-   `M2`組件不具有 APTCA 屬性，因此，不應執行或代表，都是部分信任呼叫端。

 部分信任呼叫端`X`可以呼叫方法`M1`，而導致`M1`呼叫`M2`。 因為`M2`APTCA 屬性，其立即呼叫端沒有 (`M1`) 必須滿足連結要求完全信任。`M1`具有完全信任，因此滿足這項檢查。 安全性風險是，因為`X`不會參與滿足連結要求保護`M2`來自不受信任的呼叫者。 因此，若方法具有 APTCA 屬性必須呼叫不具有屬性的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果需要 APCTA 屬性，使用需求來保護在完全信任組件呼叫的方法。 您的需求將取決於您的方法所公開的功能完全權限。 如果可能，保護以確保不會對部分信任呼叫端公開的基礎功能的完全信任要求的方法。 如果這不可行，請選取一組權限可有效保護公開的功能。 如需有關需求的詳細資訊，請參閱 <<c0> [ 需求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定，您的方法所公開的功能不會直接或間接允許來電者存取機密資訊、 作業或可以用於破壞性方式的資源。

## <a name="example"></a>範例
 下列範例會使用兩個組件和測試應用程式，說明這個規則偵測到的安全性弱點。 第一個組件並沒有 APTCA 屬性，而且應該無法存取部分信任呼叫端 (由`M2`中先前的討論)。

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>範例
 第二個組件是完全受信任，並允許部分信任呼叫端 (由`M1`中先前的討論)。

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>範例
 測試應用程式 (由`X`中先前的討論) 是以部分信任。

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 此範例會產生下列輸出。

 **要求完全信任： 要求失敗。** 
 **ClassRequiringFullTrust.DoWork 呼叫。**
## <a name="related-rules"></a>相關的規則
 [CA2117：APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫指導方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework 組件可由呼叫部分信任程式碼](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)[使用程式庫，從部分信任的程式碼](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)[需求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型化](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



