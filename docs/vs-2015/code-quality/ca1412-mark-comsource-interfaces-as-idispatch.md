---
title: CA1412：將 ComSource 介面標記為 IDispatch |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652735"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412：將 ComSource 介面標記為 IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型標記為 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 屬性，而且至少有一個指定的介面未標記為 `InterfaceIsDispatch` 值的 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 是用來識別類別公開給元件物件模型（COM）用戶端的事件介面。 這些介面必須公開為 `InterfaceIsIDispatch`，才能讓 Visual Basic 6 COM 用戶端接收事件通知。 根據預設，如果介面未以 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 屬性標示，則會公開為雙重介面。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請新增或修改 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 屬性，使其值設定為 Cominterfacetype.interfaceisidispatch，適用于使用 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 屬性指定的所有介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示一個類別，其中其中一個介面違反規則。

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>請參閱
 [如何：引發由 COM 接收所處理的事件](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)[與非受控碼互](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)操作
