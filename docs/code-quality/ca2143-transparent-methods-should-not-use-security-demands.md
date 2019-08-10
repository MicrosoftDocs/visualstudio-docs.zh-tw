---
title: CA2143:透明方法不可以使用安全性要求
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 532a10740b0617f32e4f970da8dc2a7e2807f792
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920476"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143:透明方法不可以使用安全性要求

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
透明類型或方法會以宣告方式標記<xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand`要求, <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>或方法會呼叫方法。

## <a name="rule-description"></a>規則描述
安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 安全性透明程式碼應使用完整的要求做出安全性決策，而且安全關鍵程式碼不應依賴透明程式碼提出完全要求。 執行安全性檢查的任何程式碼 (例如安全性需求), 都應該是安全關鍵。

## <a name="how-to-fix-violations"></a>如何修正違規
一般而言, 若要修正此規則的違規情形, 請使用<xref:System.Security.SecuritySafeCriticalAttribute>屬性來標記方法。 您也可以移除需求。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列程式碼上的規則檔, 因為透明方法會提出宣告式安全性需求。

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>另請參閱
[CA2142透明程式碼不應使用 Linkdemand 來保護](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)