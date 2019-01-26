---
title: CA2114:方法安全性應該是類型的超集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 63f9f6162e767d4d94bc6635cfa4bebc3c07bf12
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951452"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:方法安全性應該是類型的超集

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別具有宣告式安全性與其中一個方法已宣告式安全性是否相同的安全性動作，且安全性動作不可[連結要求](/dotnet/framework/misc/link-demands)，並沒有權限的子集這種型別所檢查的權限。檢查方法。

## <a name="rule-description"></a>規則描述
 方法不應該已經在兩個相同的動作方法層級和類型層級宣告式安全性。 不會合併兩個檢查;套用方法層級需求。 例如，如果型別要求的權限`X`，和其中一個方法會要求權限`Y`，不需要具有權限的程式碼`X`執行方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢閱您的程式碼，藉此確定這兩個動作所需。 如果這兩個動作是必要的請確定方法層級的動作，包含指定型別層級的安全性。 比方說，如果您的型別會要求權限`X`，而且它的方法也必須要求權限`Y`，此方法應該明確地要求`X`和`Y`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果方法不需要指定類型的安全性。 不過，這不是一般的案例，並可能表示需要謹慎設計檢閱。

## <a name="example-1"></a>範例 1

下列範例會使用環境的權限，來示範違反此規則的危險性。 在此範例中，應用程式程式碼會建立安全類型的執行個體之前拒絕類型所需的權限。 在真實世界的威脅的案例中，應用程式需要另一種方式取得物件的執行個體。

在下列範例中，程式庫會要求寫入類型的權限和讀取權限的方法。

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>範例 2

下列應用程式程式碼示範的程式庫的弱點可能會藉由呼叫的方法，即使它不符合類型層級安全性需求。

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