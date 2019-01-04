---
title: CA2107:必須檢閱 Deny 和 Permit Only 的使用方式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 7c8f4e108d8443816bf43dec9deb629a3a231822
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826097"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107:必須檢閱 Deny 和 Permit Only 的使用方式

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法包含指定的 PermitOnly 或 Deny 安全性動作的安全性檢查。

## <a name="rule-description"></a>規則描述
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>安全性動作應只能由有.NET Framework 安全性的進階的知識的人員。 而使用這些安全性動作的程式碼應該接受安全性檢閱。

 拒絕會改變以回應安全性需求，就會發生堆疊查核行程的預設行為。 它可讓您指定必須不被拒絕的方法，不論實際的權限，呼叫堆疊中的呼叫端的持續期間授與的權限。 如果堆疊查核行程偵測到的方法，受到拒絕，而且如果要求的權限包含在拒絕的權限時，堆疊查核行程失敗。 PermitOnly 也會改變堆疊查核行程的預設行為。 它可讓程式碼，以指定可以授與，不論呼叫端的權限的權限。 如果堆疊查核行程偵測受到 PermitOnly 方法和要求的權限不會納入 PermitOnly 所指定的權限，就會失敗的堆疊查核行程。

 這些動作所依賴的程式碼應謹慎評估有安全性弱點因為他們有限的實用性和細微的行為。 請考慮下列事項：

- [連結要求](/dotnet/framework/misc/link-demands)不會受到 Deny 或 PermitOnly。

- 如果 Deny 或 PermitOnly 發生在同一個堆疊框架會導致堆疊查核行程的需求，安全性動作會有任何作用。

- 通常可以透過多種方式指定值，用來建構路徑為基礎的權限。 拒絕存取路徑的一種形式時，不會拒絕所有形式的存取。 例如，如果檔案共用\\\Server\Share 會對應到網路磁碟機 x:，拒絕存取的檔案共用上，則必須拒絕\\\Server\Share\File、 X:\File 和每個其他存取檔案的路徑。

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>可能會達到 Deny 或 PermitOnly 之前終止，堆疊查核行程。

- 如果拒絕具有任何作用，也就是，當呼叫端具有封鎖的 Deny 權限呼叫端可以存取受保護的資源，以直接略過 Deny。 同樣地，如果呼叫端並沒有拒絕的權限，堆疊查核行程將會失敗而拒絕不。

## <a name="how-to-fix-violations"></a>如何修正違規
 任何使用這些安全性動作會造成違規。 若要修正違規情形，請勿使用這些安全性動作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在您完成安全性檢閱之後，才，則隱藏此規則的警告。

## <a name="example-1"></a>範例 1
 下列範例示範拒絕某些的限制。

 下列程式庫包含具有兩個方法，除了保護它們的安全性需求之外完全相同的類別。

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>範例 2
 下列應用程式會示範拒絕對受保護的方法，從程式庫。

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

這個範例會產生下列輸出：

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>另請參閱

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)