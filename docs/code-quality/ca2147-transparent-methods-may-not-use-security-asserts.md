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
ms.openlocfilehash: 8fa5a17e7ec1438f104c9bf2f746df26dd97ed51
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231975"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147:CA2147：透明方法不可以使用安全性判斷提示

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因
標示為<xref:System.Security.SecurityTransparentAttribute>的程式碼未授與足夠的許可權來進行判斷提示。

## <a name="rule-description"></a>規則描述
此規則會分析屬於 100% 透明或混合透明/關鍵之元件中的所有方法和類型，並將的<xref:System.Security.CodeAccessPermission.Assert%2A>任何宣告式或命令式用法標記為旗標。

在執行時間， <xref:System.Security.CodeAccessPermission.Assert%2A>從透明程式碼對的任何呼叫都會<xref:System.InvalidOperationException>導致擲回。 這可能會發生在 100% 透明元件中，而且也會出現在混合的透明/關鍵元件中，其中方法或類型已宣告為透明，但包含宣告式或命令式判斷提示。

.NET Framework 2.0 引進了名為「*透明度*」的功能。 個別方法、欄位、介面、類別和類型可以是透明或重要的。

透明程式碼不允許提升安全性許可權。 因此，授與或要求的任何許可權都會自動透過程式碼傳遞給呼叫者或主應用程式域。 提升的範例包括判斷提示、linkdemand、SuppressUnmanagedCode 和`unsafe`程式碼。

## <a name="how-to-fix-violations"></a>如何修正違規
若要解決此問題，請使用<xref:System.Security.SecurityCriticalAttribute>來標記呼叫判斷提示的程式碼，或移除該判斷提示。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則中的訊息。

## <a name="example"></a>範例
當方法擲回時`SecurityTestClass` ，如果是透明的，此程式碼將會失敗。 <xref:System.InvalidOperationException> `Assert`

[!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>範例
其中一個選項是程式碼審查下列範例中的 SecurityTransparentMethod 方法，如果方法被視為安全的提升許可權，請將 SecurityTransparentMethod 標示為安全關鍵。 這需要在方法上執行詳細、完整且無錯誤的安全性審核，並搭配在此方法的判斷提示底下發生的任何呼叫：

[!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

另一個選項是從程式碼中移除判斷提示，並讓任何後續的檔案 i/o 許可權要求流程超出 SecurityTransparentMethod 至呼叫者。 這會啟用安全性檢查。 在此情況下，不需要任何安全性審查，因為許可權要求會流向呼叫端和（或）應用程式域。 許可權要求會透過安全性原則、裝載環境和程式碼來源許可權授與來緊密控制。

## <a name="see-also"></a>另請參閱
[安全性警告](../code-quality/security-warnings.md)