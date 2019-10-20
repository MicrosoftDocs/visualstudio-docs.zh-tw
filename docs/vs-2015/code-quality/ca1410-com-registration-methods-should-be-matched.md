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
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652737"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410：應該符合 COM 註冊方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Category|Microsoft. 互通性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 類型會宣告以 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 屬性標記的方法，但不會宣告標記為 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性的方法，反之亦然。

## <a name="rule-description"></a>規則描述
 若要讓元件物件模型（COM）用戶端建立 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類型，必須先註冊該類型。 如果可以使用，則會在註冊過程中呼叫標記為 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 屬性的方法，以執行使用者指定的程式碼。 在取消註冊程式期間，會呼叫標記為 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 屬性的對應方法，以反轉登錄方法的作業。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請新增對應的註冊或取消註冊方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。 批註的程式碼會顯示違規的修正。

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1411：COM 註冊方法不應該為可見的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>請參閱
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[向 COM Regasm 註冊元件](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [（元件註冊工具）](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
