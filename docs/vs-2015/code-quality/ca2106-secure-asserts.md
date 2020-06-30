---
title: CA2106 必須：安全判斷提示 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547741"
---
# <a name="ca2106-secure-asserts"></a>CA2106:必須保護判斷提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會判斷提示使用權限，而且不會在呼叫端上執行安全性檢查。

## <a name="rule-description"></a>規則描述
 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。 當安全性許可權被判斷提示時，安全性堆疊就會停止。 如果您判斷提示許可權，但未對呼叫端執行任何檢查，呼叫者可以使用您的許可權間接執行程式碼。 只有當您確定無法以有害方式使用判斷提示時，才允許不含安全性檢查的判斷提示。 如果您呼叫的程式碼無害，或使用者無法將任意資訊傳遞給您呼叫的程式碼，則判斷提示是無害的。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將安全性需求新增至方法或其宣告類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在仔細的安全性審查之後，才隱藏此規則的警告。

## <a name="see-also"></a>另請參閱
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [安全程式碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
