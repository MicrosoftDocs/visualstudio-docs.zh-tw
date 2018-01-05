---
title: "CA1816： 呼叫 GC。SuppressFinalize 正確 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8d0287b570ed1ff5393ff0ff04b9e5d2252c29bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816：正確呼叫 GC.SuppressFinalize
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|分類|Microsoft。 使用量|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
  
-   是的實作方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   不是實作的方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   方法會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>並傳遞非 this (Me 在 Visual Basic 中)。  
  
## <a name="rule-description"></a>規則描述  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法可讓使用者在任何時間變得可用的記憶體回收的物件之前釋出資源。 如果<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>呼叫方法時，它會釋出物件的資源。 這使得最終處理不需要。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>讓記憶體回收行程不會呼叫物件的完成項。  
  
 若要防止具有完成項的衍生的類型不必重新實作<xref:System.IDisposable>並呼叫它，而不完成項的非密封的類型仍應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形：  
  
 如果方法的實作<xref:System.IDisposable.Dispose%2A>，將呼叫加入<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 如果這個方法不是實作<xref:System.IDisposable.Dispose%2A>，請移除呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>或將它移至型別的<xref:System.IDisposable.Dispose%2A>實作。  
  
 變更的所有呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>傳遞此 （我在 Visual Basic 中）。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果您 deliberating 使用，只能隱藏此規則的警告<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>控制其他物件的存留期。 請勿隱藏此規則的警告，如果實作<xref:System.IDisposable.Dispose%2A>不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。 在此情況下，無法隱藏最終處理會降低效能，並不提供任何好處。  
  
## <a name="example"></a>範例  
 下列範例顯示方法，不正確的呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範一種方法也會正確呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>請參閱  
 [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)