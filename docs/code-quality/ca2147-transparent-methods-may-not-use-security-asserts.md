---
title: CA2147:CA2147：透明方法不可以使用安全性判斷提示
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36ae392173a18796c53100599fbf5f5fb5997beb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945153"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147:CA2147：透明方法不可以使用安全性判斷提示

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 程式碼標示為<xref:System.Security.SecurityTransparentAttribute>未授與足夠的權限，來判斷提示。

## <a name="rule-description"></a>規則描述
 此規則會分析所有方法和類型中的組件是其中一個 100%透明或混合透明/關鍵，並加上旗標的任何宣告式或必要用法<xref:System.Security.CodeAccessPermission.Assert%2A>。

 在執行階段，進行任何呼叫<xref:System.Security.CodeAccessPermission.Assert%2A>從 transparent 程式碼會導致<xref:System.InvalidOperationException>擲回。 這可能會發生在兩個 100%透明的組件，以及在混合透明/關鍵組件其中方法或類型宣告為透明，但包含宣告式或必要的判斷提示中。

 .NET Framework 2.0 引進了一個功能稱為*透明度*。 透明或重要，可以是個別的方法、 欄位、 介面、 類別和類型。

 若要提高安全性權限不允許 transparent 程式碼。 因此，任何權限授與或它的要求會自動透過程式碼傳遞至呼叫端或主機的應用程式定義域。 提升權限的範例包括判斷提示、 Linkdemand、 SuppressUnmanagedCode，和`unsafe`程式碼。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要解決此問題，請將標記呼叫與判斷提示的程式碼<xref:System.Security.SecurityCriticalAttribute>，或移除判斷提示。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這項規則的訊息。

## <a name="example"></a>範例
 此程式碼將會失敗，如果`SecurityTestClass`而言是透明的當`Assert`方法會擲回<xref:System.InvalidOperationException>。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>範例
 其中一個選項是程式碼檢閱 SecurityTransparentMethod 方法，在下列範例中，並且如果方法被視為安全的提高權限，將標記 SecurityTransparentMethod 與安全關鍵。 這需要詳細、 更完整且無錯誤的安全性稽核必須對的方法，以及任何圖說進行判斷提示的方法中發生：

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 另一個選項是從程式碼中，移除判斷提示，並讓任何後續的檔案 I/O 權限要求流程之外 SecurityTransparentMethod 給呼叫者。 這可讓安全性檢查。 在此情況下，不需要任何安全性稽核，因為權限要求會流向呼叫端和/或應用程式定義域。 裝載環境，以及程式碼來源的權限授與的安全性原則，透過密切控制使用權限需求。

## <a name="see-also"></a>另請參閱
 [安全性警告](../code-quality/security-warnings.md)