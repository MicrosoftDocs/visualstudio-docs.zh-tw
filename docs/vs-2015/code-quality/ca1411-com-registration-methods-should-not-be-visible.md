---
title: CA1411： COM 註冊方法不應該為可見的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f001a2bb4920ebfb3f5cff3745639bd346a0a920
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540137"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411:COM 註冊方法不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|類別|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 以或屬性標記的方法 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 會在外部顯示。

## <a name="rule-description"></a>規則描述
 在元件物件模型中註冊元件 (COM) 時，會將專案新增至元件中每個 COM 可見類型的登錄。 以和屬性標記的方法 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 會分別在註冊和取消註冊程式期間呼叫，以執行這些類型之註冊/取消註冊專屬的使用者程式碼。 這段程式碼不應該在這些進程之外呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法的存取範圍變更為 `private` `internal`) 中的或 (`Friend` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的兩個方法。

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1410:應該和 COM 註冊方法對應](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[使用 COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (元件註冊工具](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)註冊元件) 
