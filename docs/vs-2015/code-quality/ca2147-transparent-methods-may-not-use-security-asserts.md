---
title: CA2147：透明方法不能使用安全性判斷提示 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 45639afc9946aa43df121a5a1881174371413c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546376"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147:CA2147：透明方法不可以使用安全性判斷提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 標示為的程式碼 <xref:System.Security.SecurityTransparentAttribute> 未授與足夠的許可權來判斷提示。

## <a name="rule-description"></a>規則描述
 這項規則會分析元件中的所有方法和類型，該元件中的所有方法和類型都是100% 透明或混合的透明/關鍵，並且會將的任何宣告式或命令式使用 <xref:System.Security.CodeAccessPermission.Assert%2A>

 在執行時間，從透明程式碼對的任何呼叫 <xref:System.Security.CodeAccessPermission.Assert%2A> 都會導致擲回 <xref:System.InvalidOperationException> 。 這可能會發生在100% 透明元件中，也可能發生在混合的透明/關鍵元件中，其中方法或類型宣告為透明，但包含宣告式或命令式判斷提示。

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2.0 引進了一個名為 [*透明度*] 的功能。 個別的方法、欄位、介面、類別和類型可以是透明或關鍵。

 透明程式碼不允許提升安全性許可權。 因此，授與或要求的任何許可權都會自動透過程式碼傳遞給呼叫端或主應用程式域。 提高許可權的範例包括 Assert、Linkdemand、SuppressUnmanagedCode 和 `unsafe` code。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要解決此問題，請將呼叫 Assert 的程式碼標記為 <xref:System.Security.SecurityCriticalAttribute> ，或移除判斷提示。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則中的訊息。

## <a name="example"></a>範例
 `SecurityTestClass`當方法擲回時，如果是透明的，此程式碼將會失敗 `Assert` <xref:System.InvalidOperationException> 。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>範例
 其中一個選項是在下列範例中以程式碼審核 SecurityTransparentMethod 方法，如果此方法被視為安全的提升許可權，請使用安全關鍵來標記 SecurityTransparentMethod，這需要在方法上執行詳細、完整且無錯誤的安全性審核，以及判斷提示下的方法中發生的任何調用：

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 另一個選項是從程式碼中移除判斷提示，並讓任何後續的檔案 i/o 許可權要求流程超出 SecurityTransparentMethod 至呼叫端。 這會啟用安全性檢查。 在此情況下，通常不需要安全性審核，因為許可權需求會流向呼叫端和/或應用程式域。 許可權要求是透過安全性原則、裝載環境和程式碼來源許可權授與來緊密控制。

## <a name="see-also"></a>另請參閱
 [安全性警告](../code-quality/security-warnings.md)
