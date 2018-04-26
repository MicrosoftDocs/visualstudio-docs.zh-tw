---
title: CA2107：必須檢視 Deny 和 Permit Only 的使用方式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d777379cdf5dc5d6be36989f95aadd80ca757e69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107：必須檢視 Deny 和 Permit Only 的使用方式
|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法包含指定的 PermitOnly] 或 [拒絕的安全性動作的安全性檢查。

## <a name="rule-description"></a>規則描述
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>安全性動作應只由了解進階的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]安全性。 而使用這些安全性動作的程式碼應該接受安全性檢閱。

 拒絕改變安全性要求的回應中發生堆疊查核行程的預設行為。 它可讓您指定必須不持續時間的拒絕的方法，不論實際呼叫堆疊中的呼叫端的權限授與的權限。 如果堆疊查核行程偵測到拒絕，受保護的方法，如果要求的使用權限包含在拒絕的權限，堆疊查核行程便會失敗。 PermitOnly 也會改變堆疊查核行程的預設行為。 它可讓程式碼，以指定可以授與，不論呼叫端的權限那些權限。 如果堆疊查核行程偵測 PermitOnly，受保護的方法，如果要求的使用權限不會納入 PermitOnly 所指定的權限，堆疊查核行程便會失敗。

 依賴這些動作的程式碼應該仔細評估安全性弱點因為他們有限的實用性和細微的行為。 請考慮下列事項：

-   [連結要求](/dotnet/framework/misc/link-demands)不會受到 Deny 或 PermitOnly。

-   Deny 或 permitonly 時，就會發生與會導致堆疊查核行程要求相同的堆疊框架中，如果安全性動作會有任何作用。

-   通常可以用多種方式指定用來建構路徑為基礎的權限的值。 拒絕存取路徑的一種形式並不會拒絕所有表單的存取權。 例如，如果檔案共用\\\Server\Share 對應網路磁碟機 x： 拒絕存取檔案共用上，則必須拒絕\\\Server\Share\File、 X:\File 和每一個存取檔案的其他路徑。

-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>可以達到 Deny 或 PermitOnly 之前就終止堆疊查核行程。

-   如果拒絕有任何作用，亦即當呼叫端具有封鎖的 Deny 權限呼叫端可以存取直接受保護的資源略過 Deny。 同樣地，如果呼叫端沒有拒絕的權限，堆疊查核行程會失敗，而不拒絕。

## <a name="how-to-fix-violations"></a>如何修正違規
 任何使用這些安全性動作會造成違規。 若要修正的違規情形，請勿使用這些安全性動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在您完成安全性檢閱之後，才隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範拒絕的一些限制。

 下列程式庫包含具有兩個方法，除了保護他們的安全性要求之外完全相同的類別。

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example"></a>範例
 下列應用程式會示範 Deny 的受保護之方法的效果，從程式庫。

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

 此範例會產生下列輸出。

 **需求： 拒絕呼叫者的影響不視與判斷提示的權限。** 
 **LinkDemand： 拒絕呼叫者有任何影響 LinkDemand 與判斷提示的權限。**
 **LinkDemand： 拒絕呼叫者的影響不使用 LinkDemand 保護的程式碼。**
 **LinkDemand： 此拒絕具有 LinkDemand 保護的程式碼沒有影響。**
## <a name="see-also"></a>另請參閱
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName> [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)

