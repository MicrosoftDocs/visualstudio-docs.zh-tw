---
title: CA2106:必須保護判斷提示 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0351304c2fd9ab2f581850e578828b2a297d72b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942233"
---
# <a name="ca2106-secure-asserts"></a>CA2106:必須保護判斷提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會判斷提示使用權限，而且不會在呼叫端上執行安全性檢查。

## <a name="rule-description"></a>規則描述
 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。 判斷提示安全性權限，就會停止安全性堆疊查核行程。 如果您判斷提示的權限，而不執行任何檢查呼叫端上的，呼叫端可以間接執行程式碼使用您的權限。 沒有安全性檢查允許只有很確定，判斷提示不能用於有害的方式，便會判斷提示。 判斷提示是無害的如果您呼叫的程式碼是無害的或使用者無法將任意資訊傳遞給呼叫程式碼。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入安全性要求的方法或其宣告的型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏這項規則只有在仔細的安全性檢閱之後的警告。

## <a name="see-also"></a>另請參閱
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [安全程式碼撰寫指導方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
