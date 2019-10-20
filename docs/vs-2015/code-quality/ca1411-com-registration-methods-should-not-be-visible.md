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
ms.openlocfilehash: f3ddd2c90d23884bd08a90560dcc5ed0fe700aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652719"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411：COM 註冊方法不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Category|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 以 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性標示的方法會在外部顯示。

## <a name="rule-description"></a>規則描述
 以元件物件模型（COM）註冊元件時，會將專案加入至元件中每個 COM 可見類型的登錄。 標記為 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 和 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 屬性的方法會分別在註冊和取消註冊程式期間呼叫，以執行登錄/取消註冊這些類型的特定使用者程式碼。 這段程式碼不應該在這些進程之外呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將方法的存取範圍變更為 `private` 或 `internal` （[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中的 `Friend`）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個違反規則的方法。

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1410：應該和 COM 註冊方法對應](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>請參閱
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[向 COM Regasm 註冊元件](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [（元件註冊工具）](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
