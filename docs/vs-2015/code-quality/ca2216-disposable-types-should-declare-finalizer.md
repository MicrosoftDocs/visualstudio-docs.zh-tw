---
title: CA2216：可處置的類型應該宣告完成項 |Microsoft Docs
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
ms.openlocfilehash: 5268cb90544088742c6fda7c751bab943503cacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534468"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216:可處置的類型應該宣告完成項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 實作為的型別 <xref:System.IDisposable?displayProperty=fullName> ，而且有一些欄位建議使用非受控資源，並不會依照所述的方式來執行完成項 <xref:System.Object.Finalize%2A?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 如果可處置的型別包含下列類型的欄位，就會回報此規則的違規：

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請執行呼叫您方法的完成項 <xref:System.IDisposable.Dispose%2A> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果型別不是 <xref:System.IDisposable> 為了釋出非受控資源而執行，則可以放心隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2115:使用原生資源時必須呼叫 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816:正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049:具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
