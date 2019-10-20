---
title: CA1405： COM 可見類型的基底類型應該是 COM 可見的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 13a6f80bb0500286dd44e9c5ca9378e95d4b891d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661311"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405：COM 可見類型的基底類型應該是 COM 可見
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft. 互通性|
|中斷變更|DependsOnFix|

## <a name="cause"></a>原因
 元件物件模型（COM）可見類型衍生自不是 COM 可見的類型。

## <a name="rule-description"></a>規則描述
 當 COM 可見類型在新版本中加入成員時，必須遵守嚴格的方針，以避免中斷系結至目前版本的 COM 用戶端。 COM 看不到的類型假設在加入新成員時，不需要遵循這些 COM 版本控制規則。 不過，如果 COM 可見類型衍生自 COM 不可見類型，並公開 <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的類別介面（預設值），則基底類型的所有公用成員（除非特別標示為 COM 隱藏項，也就是多餘的）會公開至通信. 如果基底類型在後續版本中加入新成員，系結至衍生類型之類別介面的任何 COM 用戶端可能會中斷。 COM 可見類型應該只衍生自 COM 可見類型，以減少中斷 COM 用戶端的機會。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將基底類型設為可見，或衍生類型 COM 不可見。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>請參閱
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[介紹類別介面](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[與非受控程式碼的互](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)操作性
