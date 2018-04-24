---
title: CA2147：透明的方法不可以使用安全性判斷提示
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a095bb50c23600aa04959db670a4038bd18cbaf1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147：透明的方法不可以使用安全性判斷提示
|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 程式碼標示為<xref:System.Security.SecurityTransparentAttribute>未授與足夠的權限，可判斷提示。

## <a name="rule-description"></a>規則描述
 此規則會分析所有方法和 100%透明或混合透明/關鍵，和的任何宣告式或必要用法加上旗標之組件中的型別<xref:System.Security.CodeAccessPermission.Assert%2A>。

 在執行階段，進行任何呼叫<xref:System.Security.CodeAccessPermission.Assert%2A>從透明程式碼會導致<xref:System.InvalidOperationException>擲回。 這可能會發生兩個 100%透明的組件，以及混合透明/關鍵的組件位置方法或類型宣告為透明，但包含的宣告式或必要的判斷提示。

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 導入了一個功能稱為*透明度*。 個別的方法、 欄位、 介面、 類別和類型可以是透明或關鍵。

 透明程式碼不可以提高安全性權限。 因此，任何權限授與或它的要求會自動傳遞執行程式碼呼叫端或主機的應用程式定義域。 提升權限的範例包括 Assert、 Linkdemand、 SuppressUnmanagedCode，和`unsafe`程式碼。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要解決此問題，請標示的程式碼會呼叫以判斷提示<xref:System.Security.SecurityCriticalAttribute>，或移除判斷提示。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的訊息。

## <a name="example"></a>範例
 如果此程式碼將會失敗`SecurityTestClass`是透明的當`Assert`方法會擲回<xref:System.InvalidOperationException>。

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>範例
 其中一個選項是程式碼檢閱 SecurityTransparentMethod 方法，在下列範例中，以及如果該方法會被視為安全的提升權限，將標記 SecurityTransparentMethod 與安全關鍵需要詳細、 更完整且沒有錯誤的安全性稽核必須連同任何圖說下，判斷提示的方法內發生方法上執行：

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 另一個選項是從程式碼移除判斷提示，並讓任何後續的檔案 I/O 的權限要求流程超出 SecurityTransparentMethod 給呼叫者。 這可讓安全性檢查。 在此情況下，沒有安全性稽核通常需要，因為權限要求會流動至呼叫端和 （或） 應用程式定義域。 裝載環境和程式碼來源的權限授與的安全性原則，透過密切控制的權限要求。

## <a name="see-also"></a>另請參閱
 [安全性警告](../code-quality/security-warnings.md)