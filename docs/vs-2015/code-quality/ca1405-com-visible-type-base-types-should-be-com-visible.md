---
title: CA1405:COM 可見類型的基底類型應該是 COM 可見 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f284c0e6e57a2ca359e765992db3f2d599fec328
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705740"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405:COM 可見類型的基底類型應該是 COM 可見
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [類別介面簡介](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[與相互操作 Unmanaged 程式碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
