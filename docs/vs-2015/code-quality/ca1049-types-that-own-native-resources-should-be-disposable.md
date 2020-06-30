---
title: CA1049：擁有原生資源的類型應該是可處置的 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546805"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049:具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|類別|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 型別會參考 <xref:System.IntPtr?displayProperty=fullName> 欄位、 <xref:System.UIntPtr?displayProperty=fullName> 欄位或 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> 欄位，但不會執行 <xref:System.IDisposable?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 此規則假設 <xref:System.IntPtr> 、 <xref:System.UIntPtr> 和 <xref:System.Runtime.InteropServices.HandleRef> 欄位儲存非受控資源的指標。 配置非受控資源的類型應該執行 <xref:System.IDisposable> ，讓呼叫端視需要釋放這些資源，並縮短保存資源之物件的存留期。

 清除非受控資源的建議設計模式是提供隱含和明確的方法 <xref:System.Object.Finalize%2A?displayProperty=fullName> ，分別使用方法和方法來釋放這些資源 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 。 <xref:System.Object.Finalize%2A>當物件判斷為無法再連線之後，垃圾收集行程會在某些不定的時間呼叫物件的方法。 <xref:System.Object.Finalize%2A>呼叫之後，需要額外的垃圾收集才能釋放物件。 <xref:System.IDisposable.Dispose%2A>方法可讓呼叫端視需要明確釋放資源，早于資源會在離開垃圾收集行程時釋放。 在清除非受控資源之後， <xref:System.IDisposable.Dispose%2A> 應該呼叫方法， <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 讓垃圾收集行程知道 <xref:System.Object.Finalize%2A> 不再需要呼叫，這樣就不需要額外的垃圾收集，並縮短物件的存留期。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請執行 <xref:System.IDisposable> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果類型未參考非受控資源，則可以安全地隱藏此規則的警告。 否則，請勿隱藏此規則的警告，因為無法執行， <xref:System.IDisposable> 可能會導致非受控資源變得無法使用或未充分利用。

## <a name="example"></a>範例
 下列範例顯示的類型，會執行 <xref:System.IDisposable> 以清除非受控資源。

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2115:使用原生資源時必須呼叫 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816:正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216:可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>另請參閱
  [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
