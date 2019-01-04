---
title: CA1405:COM 可見類型的基底類型應該是 COM 可見
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c0221231956c565eb2ce3792d0c88864b0e13e65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839319"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405:COM 可見類型的基底類型應該是 COM 可見

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|分類|Microsoft.Interoperability|
|中斷變更|DependsOnFix|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見的型別衍生自不是 COM 可見的類型。

## <a name="rule-description"></a>規則描述
 當 COM 可見型別會將成員加入新的版本中時，它必須遵守嚴格的指導方針，以避免中斷繫結至目前版本的 COM 用戶端。 COM 看不到的型別會假設它沒有加入新成員時，請遵循這些 COM 的版本控制規則。 不過，如果 COM 可見型別衍生自 COM 可見型別，會公開類別介面的<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>或<xref:System.Runtime.InteropServices.ClassInterfaceType>（預設值），基底類型的所有公用成員 （除非有特別標示為 COM 可見，這會是備援）公開至 com。 如果基底型別會加入新成員，在後續版本中，可能會中斷任何繫結至衍生型別的類別介面的 COM 用戶端。 COM 可見類型應該只從 COM 可見的類型，以降低中斷 COM 用戶端的衍生。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，讓 COM 可見的基底類型或衍生的型別 COM 變成不可見。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)