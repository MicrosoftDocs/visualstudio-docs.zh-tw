---
title: CA1415:P-Invokes 必須正確宣告。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc12d5d0a62f8d2530f13fcf860aba4e118ca4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921846"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415:P/Invokes 必須正確宣告

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|分類|Microsoft.Interoperability|
|中斷變更|不中斷-如果宣告參數的 P/Invoke 無法在元件外部看到, 則為。 中斷-如果宣告參數的 P/Invoke 可以在元件外部看到, 則為。|

## <a name="cause"></a>原因
平台叫用方法宣告不正確。

## <a name="rule-description"></a>規則描述
平台叫用方法會存取未受管理的程式碼, 並`Declare`使用或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>中的關鍵字來定義。 目前, 此規則會尋找以具有重迭結構參數指標的 Win32 函式為目標的平台叫用方法宣告, 而且對應的 managed 參數不是<xref:System.Threading.NativeOverlapped?displayProperty=fullName>結構的指標。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請正確宣告平台叫用方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則並滿足規則的平台叫用方法。

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>另請參閱
[與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)