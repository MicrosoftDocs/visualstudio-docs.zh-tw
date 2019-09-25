---
title: CA1049:具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235735"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049:具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因

型別會參考<xref:System.IntPtr?displayProperty=fullName>欄位<xref:System.UIntPtr?displayProperty=fullName> 、欄位或<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>欄位，但不會執行<xref:System.IDisposable?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述

此規則假設<xref:System.IntPtr>、 <xref:System.UIntPtr>和<xref:System.Runtime.InteropServices.HandleRef>欄位儲存非受控資源的指標。 配置非受控資源的類型應該<xref:System.IDisposable>執行，讓呼叫端視需要釋放這些資源，並縮短保存資源之物件的存留期。

清除非受控資源的建議設計模式是提供隱含和明確的方法，分別使用<xref:System.Object.Finalize%2A?displayProperty=fullName>方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>和方法來釋放這些資源。 當物件判斷為無法<xref:System.Object.Finalize%2A>再連線之後，垃圾收集行程會在某些不定的時間呼叫物件的方法。 呼叫<xref:System.Object.Finalize%2A>之後，需要額外的垃圾收集才能釋放物件。 <xref:System.IDisposable.Dispose%2A>方法可讓呼叫端視需要明確釋放資源，早于資源會在離開垃圾收集行程時釋放。 在清除非受控資源之後， <xref:System.IDisposable.Dispose%2A>應該<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>呼叫方法，讓垃圾收集行程知道<xref:System.Object.Finalize%2A>不再需要呼叫它，這可免除額外垃圾收集的需求，並縮短物件的存留期。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請<xref:System.IDisposable>執行。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果類型未參考非受控資源，則可以安全地隱藏此規則的警告。 否則，請勿隱藏此規則的警告，因為無法執行<xref:System.IDisposable> ，可能會導致非受控資源變得無法使用或未充分利用。

## <a name="example"></a>範例
下列範例顯示的類型，會<xref:System.IDisposable>執行以清除非受控資源。

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>相關規則
[CA2115呼叫 GC。使用原生資源時的 KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816呼叫 GC。Gc.suppressfinalize 正確](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>另請參閱

- [清除 Unmanaged 資源](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)