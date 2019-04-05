---
title: CA1408:不要使用 AutoDual ClassInterfaceType |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2f59b8f09fb8ce15af407981aa9dccdeb008b3b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944046"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408:不要使用 AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見的型別會標示<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性設為`AutoDual`的值<xref:System.Runtime.InteropServices.ClassInterfaceType>。

## <a name="rule-description"></a>規則描述
 使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設，如果<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性未指定，會使用僅分派介面。

 除非已標記，否則所有公用的非泛型型別會顯示為 COM;所有的非公用和泛型型別都看不到 COM

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將變更的值<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性設定為`None`的值<xref:System.Runtime.InteropServices.ClassInterfaceType>明確定義介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告，除非它是特定類型和其基底類型的配置不會在未來版本中變更。

## <a name="example"></a>範例
 下列範例顯示違反此規則，並重新宣告要使用明確的介面之類別的類別。

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1403:自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412:ComSource 介面標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>另請參閱
 [類別介面簡介](http://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[限定互通的.NET 類型](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)[與相互操作 Unmanaged 程式碼](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
