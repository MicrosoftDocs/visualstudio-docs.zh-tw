---
title: CA2106：必須保護判斷提示
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ff16cdce4be04bd076c93763fb6a22d2721675f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551778"
---
# <a name="ca2106-secure-asserts"></a>CA2106：必須保護判斷提示

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會判斷提示權限，而且不會執行安全性檢查呼叫端上。

## <a name="rule-description"></a>規則描述
 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。 判斷提示安全性權限，就會停止安全性堆疊查核行程。 如果您判斷提示的權限，而不執行任何檢查呼叫端上的，呼叫端可以間接執行程式碼使用您的權限。 允許您是否確定判斷提示不能用於有害的方式沒有安全性檢查，便會判斷提示。 如果您呼叫的程式碼是無害的則使用者無法將任意資訊傳遞給呼叫程式碼，判斷提示是無害的。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入安全性要求的方法或其宣告的型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏這項規則只有在仔細的安全性檢閱之後的警告。

## <a name="see-also"></a>另請參閱

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)