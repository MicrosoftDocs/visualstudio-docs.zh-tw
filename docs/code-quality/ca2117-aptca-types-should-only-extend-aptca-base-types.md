---
title: "CA2117: APTCA 類型應該只擴充 APTCA 基底類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5619de2512e18cbe9d7dbfb3d992886ae23a25bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117：APTCA 類型應該只擴充 APTCA 基底類型
|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的類型與組件中<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>屬性繼承自沒有屬性的組件中宣告的型別。  
  
## <a name="rule-description"></a>規則描述  
 根據預設，使用強式名稱的組件中的公用或受保護類型隱含地受到[繼承要求](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)完全信任。 強式名稱組件標示<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性並沒有這項保護。 屬性會停用繼承要求。 這可讓組件中宣告繼承公開型別沒有完全信任的類型。  
  
 當 APTCA 屬性完全受信任的組件，並且組件中的類型會繼承自不允許部分信任呼叫端的型別時，產生安全性弱點有可能。 如果兩種型別`T1`和`T2`符合下列條件，惡意呼叫端可以使用類型`T1`略過隱含完全信任的繼承要求保護`T2`:  
  
-   `T1`具有 APTCA 屬性的完全信任組件中宣告的公用型別。  
  
-   `T1`繼承自型別`T2`組件外部。  
  
-   `T2`組件沒有 APTCA 屬性，因此，不能由部分信任組件中的型別可繼承。  
  
 部分信任的型別`X`可以繼承自`T1`，讓它存取宣告中的繼承成員`T2`。 因為`T2`沒有 APTCA 屬性，其立即的衍生類型 (`T1`) 必須符合繼承要求完全信任。`T1`具有完全信任，因此會滿足這項檢查。 安全性風險是因為`X`不會參與滿足繼承要求保護`T2`來自不受信任的子類別化。 基於這個理由，具有 APTCA 屬性的型別必須延伸不具有屬性的型別。  
  
 另一個安全性問題，並可能是較常見的一個，是衍生型別 (`T1`) 可以透過程式設計錯誤公開受保護的成員，從需要完全信任的型別 (`T2`)。 當發生這種情況時，不受信任的呼叫端存取應只提供給完全受信任的類型的資訊。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 不需要的 APTCA 屬性之組件中的違規所回報該類型時，請將它移除。  
  
 如果需要 APTCA 屬性，加入類型繼承要求完全信任。 這可防止不受信任的類型繼承。  
  
 您可修正的違規情形，加入基底類型的違規所報告的組件的 APTCA 屬性。 不要這樣不含第一個執行的組件中的所有程式碼和所有相依於組件的程式碼需要大量的安全性檢閱。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 若要安全地隱藏此規則的警告，您必須確定，您的型別公開的受保護的成員不直接或間接允許執行未受信任的呼叫端存取機密資訊、 作業或資源，可用於破壞性的方式。  
  
## <a name="example"></a>範例  
 下列範例會使用兩個組件和測試應用程式，說明這個規則偵測到的安全性弱點。 第一個組件並沒有 APTCA 屬性，而不是可由部分信任的類型繼承 (由`T2`在先前的討論內容)。  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>範例  
 第二個組件，由`T1`在先前的討論中，受到完全信任，並允許部分信任呼叫端。  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>範例  
 測試類型，由`X`在先前的討論中，是在部分信任組件中。  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 此範例會產生下列輸出。  
  
 **符合 shady glen 在 2003 年 2 月 22 日 12:00:00 AM ！**  
**從測試： Sunny 草原**  
**符合 sunny 草原在 2003 年 2 月 22 日 12:00:00 AM ！**   
## <a name="related-rules"></a>相關的規則  
 [CA2116：APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)   
 [.NET framework 組件可由部分信任程式碼](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [從部分受信任程式碼使用程式庫](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
 [繼承要求](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)