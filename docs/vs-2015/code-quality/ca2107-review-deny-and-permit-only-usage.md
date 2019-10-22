---
title: CA2107 必須：審查拒絕並僅允許使用方式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 32339852d67d4f3f28fedd204a056440ad49e075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665958"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107：必須檢視 Deny 和 Permit Only 的使用方式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法包含指定 PermitOnly 或 Deny 安全性動作的安全性檢查。

## <a name="rule-description"></a>規則描述
 只有具備 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 安全性之 advanced 知識的使用者，才應該使用[PermitOnly 方法](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)和 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> 的安全性動作。 而使用這些安全性動作的程式碼應該接受安全性檢閱。

 [拒絕] 會改變回應安全性需求時，所發生之堆疊逐步解說的預設行為。 它可讓您指定拒絕方法期間不得授與的許可權，而不論呼叫堆疊中呼叫端的實際許可權為何。 如果堆疊演練偵測到受拒絕保護的方法，而且如果要求的許可權包含在拒絕的許可權中，堆疊的逐步解說就會失敗。 PermitOnly 也會改變堆疊逐步解說的預設行為。 它可讓程式碼只指定可授與的許可權，而不論呼叫端的許可權為何。 如果堆疊逐步解說偵測到受到 PermitOnly 保護的方法，而且如果要求的許可權未包含在 PermitOnly 所指定的許可權中，堆疊就會失敗。

 依賴這些動作的程式碼應該仔細評估是否有安全性弱點，因為其實用性和細微行為有限。 請考慮下列事項：

- [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)不會受到拒絕或 PermitOnly 的影響。

- 如果拒絕或 PermitOnly 發生在造成堆疊引導的需求所在的相同堆疊框架中，安全性動作就不會有任何作用。

- 用來建立路徑型許可權的值通常可以用多種方式來指定。 拒絕存取某一種形式的路徑並不會拒絕所有表單的存取。 例如，如果 \\ \Server\Share 的檔案共用對應到網路磁碟機 X：，若要拒絕存取共用上的檔案，您必須拒絕 \\ \Server\Share\File、X:\File，以及存取該檔案的所有其他路徑。

- @No__t_0 可以在達到拒絕或 PermitOnly 之前，終止堆疊的逐步解說。

- 如果拒絕有任何作用，亦即，當呼叫者具有拒絕的許可權時，呼叫端可以直接存取受保護的資源，略過拒絕。 同樣地，如果呼叫端沒有拒絕的許可權，堆疊的逐步執行就會失敗，而不會有拒絕。

## <a name="how-to-fix-violations"></a>如何修正違規
 任何使用這些安全性動作都會導致違規。 若要修正違規，請勿使用這些安全性動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在您完成安全性審查之後，才會隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範拒絕的一些限制。

 下列程式庫所包含的類別有兩個相同的方法，但保護它們的安全性要求除外。

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>範例
 下列應用程式會示範拒絕程式庫中受保護的方法所造成的影響。

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 此範例會產生下列輸出。

 **需求：呼叫者的拒絕不會影響具有判斷提示許可權的要求。** 
**linkdemand：呼叫端的 deny 不會影響具有判斷提示許可權的 linkdemand。** 
**linkdemand：呼叫端的 deny 不會影響受 LinkDemand 保護的程式碼。** 
**LinkDemand：此拒絕沒有作用受 LinkDemand 保護的程式碼。**
## <a name="see-also"></a>請參閱
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [使用 PermitOnly 方法](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)覆[寫安全性檢查](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28)的[安全程式碼撰寫指導方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
