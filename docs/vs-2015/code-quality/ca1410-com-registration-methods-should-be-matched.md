---
title: CA1410:應該和 COM 註冊方法對應 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd47aa57d128ec5f88f77036546476128aae39f5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692064"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410:應該和 COM 註冊方法對應
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 型別宣告以標記的方法<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>屬性，但不宣告的方法，以標記<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>屬性，反之亦然。

## <a name="rule-description"></a>規則描述
 若要建立的元件物件模型 (COM) 用戶端[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]型別，必須先註冊型別。 如果有的話，會以標記的方法<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>期間註冊程序來執行使用者指定的程式碼會呼叫屬性。 對應的方法會標示為<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>屬性會取消註冊程序期間呼叫的註冊方法的作業。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入相對應的登錄或取消登錄方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。 加上註解的程式碼會顯示違規的修正。

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1411:COM 註冊方法不應該為可見](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [向 COM 註冊組件](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe （組件登錄工具）](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
