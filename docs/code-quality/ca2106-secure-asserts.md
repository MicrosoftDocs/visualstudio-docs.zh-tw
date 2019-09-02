---
title: CA2106:必須保護判斷提示
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df19d31abe88c6d12bafc933ba740badb832eb16
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921077"
---
# <a name="ca2106-secure-asserts"></a>CA2106:必須保護判斷提示

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
方法會判斷提示許可權, 且不會對呼叫端執行任何安全性檢查。

## <a name="rule-description"></a>規則描述
判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。 當安全性許可權被判斷提示時, 安全性堆疊就會停止。 如果您判斷提示許可權, 但未對呼叫端執行任何檢查, 呼叫者可以使用您的許可權間接執行程式碼。 如果您確定無法以有害方式使用判斷提示, 則允許不含安全性檢查的判斷提示。 如果您呼叫的程式碼無害, 或使用者無法將任意資訊傳遞給您呼叫的程式碼, 則判斷提示是無害的。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請將安全性需求新增至方法或其宣告類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
只有在仔細的安全性審查之後, 才隱藏此規則的警告。

## <a name="see-also"></a>另請參閱

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)