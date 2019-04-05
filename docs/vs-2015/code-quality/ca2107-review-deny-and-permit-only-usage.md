---
title: CA2107:檢視 deny 和 permit only 的使用方式 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 425a7363e03dcc8a967853bbe574f29678df11a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941530"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107:必須檢閱 Deny 和 Permit Only 的使用方式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法包含指定的 PermitOnly 或 Deny 安全性動作的安全性檢查。

## <a name="rule-description"></a>規則描述
 [使用 PermitOnly 方法](http://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)並<xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>安全性動作應只由具備進階的知識的人的[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]安全性。 而使用這些安全性動作的程式碼應該接受安全性檢閱。

 拒絕會改變以回應安全性需求，就會發生堆疊查核行程的預設行為。 它可讓您指定必須不被拒絕的方法，不論實際的權限，呼叫堆疊中的呼叫端的持續期間授與的權限。 如果堆疊查核行程偵測到的方法，受到拒絕，而且如果要求的權限包含在拒絕的權限時，堆疊查核行程失敗。 PermitOnly 也會改變堆疊查核行程的預設行為。 它可讓程式碼，以指定可以授與，不論呼叫端的權限的權限。 如果堆疊查核行程偵測受到 PermitOnly 方法和要求的權限不會納入 PermitOnly 所指定的權限，就會失敗的堆疊查核行程。

 這些動作所依賴的程式碼應謹慎評估有安全性弱點因為他們有限的實用性和細微的行為。 請考慮下列事項：

-   [連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)不會受到 Deny 或 PermitOnly。

-   如果 Deny 或 PermitOnly 發生在同一個堆疊框架會導致堆疊查核行程的需求，安全性動作會有任何作用。

-   通常可以透過多種方式指定值，用來建構路徑為基礎的權限。 拒絕存取路徑的一種形式時，不會拒絕所有形式的存取。 例如，如果檔案共用\\\Server\Share 會對應到網路磁碟機 x:，拒絕存取的檔案共用上，則必須拒絕\\\Server\Share\File、 X:\File 和每個其他存取檔案的路徑。

-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>可能會達到 Deny 或 PermitOnly 之前終止，堆疊查核行程。

-   如果拒絕具有任何作用，也就是，當呼叫端具有封鎖的 Deny 權限呼叫端可以存取受保護的資源，以直接略過 Deny。 同樣地，如果呼叫端並沒有拒絕的權限，堆疊查核行程將會失敗而拒絕不。

## <a name="how-to-fix-violations"></a>如何修正違規
 任何使用這些安全性動作會造成違規。 若要修正違規情形，請勿使用這些安全性動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在您完成安全性檢閱之後，才，則隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範拒絕某些的限制。

 下列程式庫包含具有兩個方法，除了保護它們的安全性需求之外完全相同的類別。

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>範例
 下列應用程式會示範拒絕對受保護的方法，從程式庫。

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 此範例會產生下列輸出。

 **需求：呼叫端的拒絕具有不使用判斷提示的權限需求會影響。** 
 **LinkDemand 的比較：拒絕呼叫端的無關 LinkDemand 的比較與判斷提示的權限。** 
 **LinkDemand 的比較：拒絕呼叫者的影響不使用 LinkDemand 保護的程式碼。** 
 **LinkDemand 的比較：此拒絕影響不使用 LinkDemand 保護的程式碼。**
## <a name="see-also"></a>另請參閱
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [安全程式碼撰寫指導方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[覆寫安全性檢查](http://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28)[使用 PermitOnly 方法](http://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
