---
title: CA1411:COM 註冊方法不應該為可見的
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9582fb6bbdbda8aefbb60e2c69d16380eec3dff
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234749"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411:COM 註冊方法不應該為可見的

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|分類|Microsoft.Interoperability|
|重大變更|中斷|

## <a name="cause"></a>原因

<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 以<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>或屬性標記的方法會在外部顯示。

## <a name="rule-description"></a>規則描述
以元件物件模型（COM）註冊元件時，會將專案加入至元件中每個 COM 可見類型的登錄。 標記<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>為和<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>屬性的方法會分別在註冊和取消註冊程式期間呼叫，以執行登錄/取消註冊這些類型的特定使用者程式碼。 這段程式碼不應該在這些進程之外呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請將方法的存取範圍變更`private`為`internal`或`Friend` （ [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]在中為）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示兩個違反規則的方法。

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1410COM 註冊方法應符合](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [向 COM 註冊組件](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (組件登錄工具)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)