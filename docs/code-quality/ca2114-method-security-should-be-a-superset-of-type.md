---
title: CA2114:方法安全性應該是類型的超集
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d83da42a029d746899bfaccf5d62f8856a040611
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921108"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:方法安全性應該是類型的超集

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
型別具有宣告式安全性, 其中一個方法具有相同安全性動作的宣告式安全性, 而且安全性動作不是[連結要求](/dotnet/framework/misc/link-demands), 而由型別檢查的許可權不是方法所檢查的許可權子集。

## <a name="rule-description"></a>規則描述
方法不應該同時具有相同動作的方法層級和類型層級宣告式安全性。 這兩個檢查不會合並;只會套用方法層級的要求。 例如, 如果某個型別要求許可權`X`, 而其中一個方法要求許可權`Y`, 則程式碼不必擁有執行方法的`X`許可權。

## <a name="how-to-fix-violations"></a>如何修正違規
請檢查您的程式碼, 以確定這兩個動作都是必要的。 如果這兩個動作都是必要的, 請確定方法層級動作包含在類型層級指定的安全性。 例如, 如果您的型別要求`X`許可權, 而且其方法也必須要求`Y`許可權, 則方法應該明確`X`地`Y`要求和。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果方法不需要類型所指定的安全性, 則可以安全地隱藏此規則的警告。 不過, 這不是一般案例, 而且可能表示需要謹慎的設計審查。

## <a name="example-1"></a>範例 1

下列範例會使用環境許可權來示範違反此規則的危險。 在此範例中, 應用程式程式碼會先建立安全類型的實例, 再拒絕該類型所需的許可權。 在真實世界的威脅案例中, 應用程式需要另一種方式來取得物件的實例。

在下列範例中, 程式庫會要求類型的寫入權限, 以及方法的讀取權限。

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>範例 2

下列應用程式代碼會藉由呼叫方法來示範程式庫的弱點, 即使它不符合類型層級的安全性需求也一樣。

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

這個範例會產生下列輸出：

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [連結要求](/dotnet/framework/misc/link-demands)
- [資料與模型化](/dotnet/framework/data/index)