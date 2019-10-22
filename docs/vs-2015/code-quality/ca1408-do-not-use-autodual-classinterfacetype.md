---
title: CA1408：不要使用 AutoDual ClassInterfaceType |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ccd8f9fa201e2cdfabfb7f6354d6df4718c572e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652760"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408：不要使用 AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型（COM）可見類型已標記為 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性設定為 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的 `AutoDual` 值。

## <a name="rule-description"></a>規則描述
 使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設，如果未指定 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性，則會使用分派專用介面。

 除非另有標示，否則 COM 可以看見所有公用非泛型型別;COM 不會看到所有非公用和泛型型別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性的值變更為 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的 `None` 值，並明確定義介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非確定類型的配置及其基底類型的配置不會在未來版本中變更，否則請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的類別會違反規則，並將類別的重新宣告為使用明確的介面。

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1403：自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412：ComSource 介面必須標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>請參閱
 [簡介類別介面](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[適用于互通的 .net 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)可[與非受控程式碼互](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)操作
