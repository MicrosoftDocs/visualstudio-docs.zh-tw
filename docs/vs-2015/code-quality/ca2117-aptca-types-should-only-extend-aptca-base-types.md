---
title: CA2117： APTCA 類型應該只擴充 APTCA 基底類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09fa055fbf1b11e06b1dde32df5a316a3ec39848
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658663"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117：APTCA 類型應該只擴充 APTCA 基底類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 具有 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 屬性之元件中的公用或受保護型別，會繼承自不具有該屬性之元件中所宣告的型別。

## <a name="rule-description"></a>規則描述
 根據預設，具有強式名稱之元件中的公用或受保護類型，會由完全信任的[繼承要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)隱含保護。 以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性標記的強式名稱元件沒有此保護。 屬性會停用繼承要求。 這會讓在元件中宣告的公開類型可由不具有完全信任的類型繼承。

 當 APTCA 屬性出現在完全信任的元件上，且元件中的類型繼承自不允許部分信任呼叫端的類型時，可能會發生安全性攻擊。 如果 `T1` 和 `T2` 的兩個類型符合下列條件，惡意呼叫端可以使用類型 `T1` 來略過保護 `T2` 的隱含完全信任繼承要求：

- `T1` 是在具有 APTCA 屬性的完全信任元件中宣告的公用類型。

- `T1` 繼承自其元件外部的類型 `T2`。

- `T2` 的元件沒有 APTCA 屬性，因此不應該由部分信任元件中的類型繼承。

  部分信任的類型 `X` 可以繼承自 `T1`，讓它能夠存取在 `T2` 中宣告的繼承成員。 因為 `T2` 沒有 APTCA 屬性，所以其直屬衍生型別（`T1`）必須滿足完全信任的繼承要求;`T1` 有完全信任，因此可滿足這種檢查。 安全性風險是因為 `X` 並未參與滿足繼承要求的需求，保護 `T2` 不受信任的子類別。 基於這個理由，具有 APTCA 屬性的類型不能擴充沒有屬性的類型。

  另一個安全性問題（可能是更常見的一項）是，衍生的型別（`T1`）可以透過程式設計人員錯誤，從需要完全信任的型別（`T2`）公開受保護的成員。 發生這種情況時，不受信任的呼叫端會取得僅適用于完全信任類型之資訊的存取權。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果違規所報告的型別是在不需要 APTCA 屬性的元件中，請將它移除。

 如果需要 APTCA 屬性，請將完全信任的繼承要求加入至類型。 這可防止不受信任類型的繼承。

 藉由將 APTCA 屬性加入違規所報告之基底類型的元件中，可以修正違規。 不需要先對元件中的所有程式碼進行大量的安全性審查，以及相依于元件的所有程式碼，就不要執行此動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏這項規則的警告，您必須確保您的類型所公開的受保護成員不會直接或間接允許未受信任的呼叫者存取可以破壞性方式使用的機密資訊、作業或資源。

## <a name="example"></a>範例
 下列範例會使用兩個元件和一個測試應用程式來說明此規則偵測到的安全性弱點。 第一個元件沒有 APTCA 屬性，而且不應該由部分信任的類型（在先前討論中以 `T2` 表示）繼承。

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>範例
 第二個元件（在先前討論中是由 `T1` 表示）完全受信任，並允許部分信任的呼叫端。

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>範例
 在上一個討論中，由 `X` 表示的測試類型是在部分信任的元件中。

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 此範例會產生下列輸出。

 **開會 shady glen 2/22/2003 12:00:00 AM！** **來自測試的 
： sunny meadow** 
**符合 SUNNY meadow 2/22/2003 12:00:00 AM！**
## <a name="related-rules"></a>相關規則
 [CA2116：APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>請參閱
 [安全](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)程式碼撰寫方針[.NET Framework 元件](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d)可使用部分信任程式碼[繼承要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)的連結[庫](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)來呼叫
