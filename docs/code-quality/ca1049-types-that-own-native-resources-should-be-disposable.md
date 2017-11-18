---
title: "CA1049： 擁有原生資源的類型應該是可處置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ebcb3325cfefdfeeb95b30477c4b266a70f40eb0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049：擁有原生資源的類型應為可處置
|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 型別參考<xref:System.IntPtr?displayProperty=fullName> 欄位中， <xref:System.UIntPtr?displayProperty=fullName>  欄位中，或<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>欄位，但未實作<xref:System.IDisposable?displayProperty=fullName>。  
  
## <a name="rule-description"></a>規則描述  
 這項規則假設<xref:System.IntPtr>， <xref:System.UIntPtr>，和<xref:System.Runtime.InteropServices.HandleRef>欄位儲存 unmanaged 資源的指標。 配置 unmanaged 的資源的類型應實作<xref:System.IDisposable>讓呼叫端需要釋放這些資源上要求及縮短持有資源之物件存留期。  
  
 若要清除 unmanaged 資源的建議的設計模式是提供隱含和明確的方法來釋放這些資源使用<xref:System.Object.Finalize%2A?displayProperty=fullName>方法和<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法，分別。 記憶體回收行程呼叫<xref:System.Object.Finalize%2A>物件確定可連線後一些不定時間在物件的方法。 之後<xref:System.Object.Finalize%2A>呼叫時，額外記憶體回收，才能釋放的物件。 <xref:System.IDisposable.Dispose%2A>方法可讓呼叫端明確釋放資源的需求，會釋出資源，如果記憶體回收行程保留之前。 它會清除 unmanaged 資源之後,<xref:System.IDisposable.Dispose%2A>應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>方法，讓記憶體回收行程知道<xref:System.Object.Finalize%2A>不再具有呼叫; 這就不需要額外的記憶體回收，並縮短物件存留期。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，實作<xref:System.IDisposable>。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果類型未參考的 unmanaged 的資源。 否則，請勿隱藏此規則的警告因為沒有實作<xref:System.IDisposable>可能會導致變成無法使用或未充分使用的 unmanaged 的資源。  
  
## <a name="example"></a>範例  
 下列範例示範實作的型別<xref:System.IDisposable>清除 unmanaged 資源。  
  
 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2115：使用原生資源時必須呼叫 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001：具有可處置欄位的類型應該是可處置的](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## <a name="see-also"></a>另請參閱  
 [清除 Unmanaged 資源](/dotnet/standard/garbage-collection/unmanaged)   
 [處置模式](/dotnet/standard/design-guidelines/dispose-pattern)