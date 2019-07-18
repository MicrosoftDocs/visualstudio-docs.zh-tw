---
title: CA1410:應該和 COM 註冊方法對應
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a424e3c884d47b7deb848b418fbf0f3344d6c379
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714727"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410:應該和 COM 註冊方法對應

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因

型別宣告以標記的方法<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>屬性，但不宣告的方法，以標記<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>屬性，反之亦然。

## <a name="rule-description"></a>規則描述

元件物件模型 (COM) 用戶端可以建立.NET 型別，必須先註冊型別。 如果有的話，會以標記的方法<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>期間註冊程序來執行使用者指定的程式碼會呼叫屬性。 對應的方法會標示為<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>屬性會取消註冊程序期間呼叫的註冊方法的作業。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，加入相對應的登錄或取消登錄方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的型別。 加上註解的程式碼會顯示違規的修正。

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>相關的規則

[CA1411:COM 註冊方法不應該為可見](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [向 COM 註冊組件](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (組件登錄工具)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)