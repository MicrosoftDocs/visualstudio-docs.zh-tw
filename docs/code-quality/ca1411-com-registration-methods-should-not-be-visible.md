---
title: CA1411：COM 註冊方法不應該為可見的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0cd599ee67182084e7f2fb663d343281b0a8b079
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551703"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411：COM 註冊方法不應該為可見的

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|類別|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因

方法標記著<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>或<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>屬性是外部可見。

## <a name="rule-description"></a>規則描述
 組件註冊時使用元件物件模型 (COM)，每個 COM 可見的型別組件中的登錄中加入項目。 方法標記著<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>和<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>屬性進行註冊和取消註冊程序，分別稱為，若要執行的註冊/取消註冊這些類型的特定使用者程式碼。 此程式碼不應該呼叫這些程序之外。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更方法的可及性`private`或是`internal`(`Friend`在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩種方法違反此規則。

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1410：應該和 COM 註冊方法對應](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [向 COM 註冊組件](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (組件登錄工具)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)