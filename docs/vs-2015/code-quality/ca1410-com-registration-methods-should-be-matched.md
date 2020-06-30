---
title: CA1410： COM 註冊方法應符合 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546701"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410:應該和 COM 註冊方法對應
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|類別|Microsoft. 互通性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 類型會宣告以屬性標記的方法， <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 但不會宣告以屬性標記的方法 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> ，反之亦然。

## <a name="rule-description"></a>規則描述
 若要讓元件物件模型（COM）用戶端建立 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類型，必須先註冊該類型。 如果可以使用，則會在 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 註冊過程中呼叫以屬性標記的方法，以執行使用者指定的程式碼。 在取消註冊的過程中，會呼叫以屬性標記的對應方法， <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 以反轉登錄方法的作業。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請新增對應的註冊或取消註冊方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。 批註的程式碼會顯示違規的修正。

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1411:COM 註冊方法不應該為可見的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[向 COMRegasm.exe 註冊元件](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [（元件註冊工具）](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
