---
title: CA2216:可處置的類型應該宣告完成項 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 082afacba1ccf4c982e5ddceec37d2a1567efd7a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651656"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216:可處置的類型應該宣告完成項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|分類|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 一個型別，它會執行 <xref:System.IDisposable?displayProperty=fullName>，而且有一些欄位會建議使用非受控資源，而不會如 <xref:System.Object.Finalize%2A?displayProperty=fullName> 所述來實作為完成項。

## <a name="rule-description"></a>規則描述
 如果可處置的類型包含下列類型的欄位，則會報告此規則的違規：

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請執行呼叫 <xref:System.IDisposable.Dispose%2A> 方法的完成項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果類型未針對釋放非受控資源的目的而執行 <xref:System.IDisposable>，則可放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2115：呼叫 GC。使用原生資源時的 KeepAlive ](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816：呼叫 GC。Gc.suppressfinalize 正確 ](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049：擁有原生資源的類型應該是可處置的 ](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
