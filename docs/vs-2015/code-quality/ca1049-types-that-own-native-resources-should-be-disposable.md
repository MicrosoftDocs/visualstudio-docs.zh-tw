---
title: CA1049:擁有原生資源應該是可處置的類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 628a50a66c973020ff62d8041672901b2a578d31
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944565"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049:具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 參考型別<xref:System.IntPtr?displayProperty=fullName> 欄位中， <xref:System.UIntPtr?displayProperty=fullName>  欄位中，或有<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>欄位中，但未實作<xref:System.IDisposable?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 這項規則假設<xref:System.IntPtr>， <xref:System.UIntPtr>，和<xref:System.Runtime.InteropServices.HandleRef>欄位儲存 unmanaged 資源的指標。 配置 unmanaged 的資源的類型應實作<xref:System.IDisposable>，讓呼叫者以釋出那些資源需求，並縮短持有資源物件的存留期。

 清除 unmanaged 資源的建議的設計模式是提供隱含和明確的方法來釋放這些資源，使用<xref:System.Object.Finalize%2A?displayProperty=fullName>方法和<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法，分別。 記憶體回收行程呼叫<xref:System.Object.Finalize%2A>之後物件判斷為不會再連線到某個不定時間點物件的方法。 之後<xref:System.Object.Finalize%2A>呼叫時，額外記憶體回收，才能釋放物件。 <xref:System.IDisposable.Dispose%2A>方法可讓呼叫端明確釋放依需求，會釋放資源，如果記憶體回收行程保留先前的資源。 它會清除的 unmanaged 資源之後,<xref:System.IDisposable.Dispose%2A>應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>方法，讓記憶體回收行程知道<xref:System.Object.Finalize%2A>再也不需要呼叫; 這就不需要額外的回收，並縮短物件存留期。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作<xref:System.IDisposable>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果類型未參考 unmanaged 的資源。 否則，請勿隱藏此規則的警告因為實作<xref:System.IDisposable>可能會導致變成無法使用或未充分使用的 unmanaged 的資源。

## <a name="example"></a>範例
 下列範例示範實作的類型<xref:System.IDisposable>清除 unmanaged 資源。

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2115:呼叫 GC。KeepAlive 時使用原生資源](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816:呼叫 GC。SuppressFinalize 正確](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216:可處置類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>另請參閱
  [Dispose 模式](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
