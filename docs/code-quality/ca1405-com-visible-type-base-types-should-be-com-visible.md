---
title: CA1405:COM 可見類型的基底類型應該是 COM 可見
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234961"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405:COM 可見類型的基底類型應該是 COM 可見

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|分類|Microsoft.Interoperability|
|重大變更|DependsOnFix|

## <a name="cause"></a>原因
元件物件模型（COM）可見類型衍生自不是 COM 可見的類型。

## <a name="rule-description"></a>規則描述
當 COM 可見類型在新版本中加入成員時，必須遵守嚴格的方針，以避免中斷系結至目前版本的 COM 用戶端。 COM 看不到的類型假設在加入新成員時，不需要遵循這些 COM 版本控制規則。 不過，如果 com 可見型別衍生自 com 不可見型別，並公開<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>或<xref:System.Runtime.InteropServices.ClassInterfaceType>的類別介面（預設值），則基底型別的所有公用成員（除非特別標示為 COM 隱藏，而這會是多餘的）會公開至 COM。 如果基底類型在後續版本中加入新成員，系結至衍生類型之類別介面的任何 COM 用戶端可能會中斷。 COM 可見類型應該只衍生自 COM 可見類型，以減少中斷 COM 用戶端的機會。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請將基底類型設為可見，或衍生類型 COM 不可見。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的類型。

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)