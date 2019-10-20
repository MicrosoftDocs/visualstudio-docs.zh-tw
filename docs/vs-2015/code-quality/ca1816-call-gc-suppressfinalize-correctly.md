---
title: CA1816：呼叫 GC。Gc.suppressfinalize 正確 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668390"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816：正確呼叫 GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因

- 執行 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 的方法不會呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

- 不是 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 執行的方法。

- 方法會呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 並傳遞這個以外的內容（我在 Visual Basic 中）。

## <a name="rule-description"></a>規則描述
 @No__t_0 方法可讓使用者在物件變成可供垃圾收集之前，隨時釋放資源。 如果呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法，它就會釋出物件的資源。 這會導致不必要的終止。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 應該呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>，讓垃圾收集行程不會呼叫物件的完成項。

 若要防止具有完成項的衍生類型必須重新執行 [IDisposable] （<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->）並呼叫它時，沒有完成項的未密封類型仍應呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規：

 如果方法是 <xref:System.IDisposable.Dispose%2A> 的執行，請將呼叫新增至 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

 如果方法不是 <xref:System.IDisposable.Dispose%2A> 的執行，請移除對 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的呼叫，或將它移至類型的 <xref:System.IDisposable.Dispose%2A> 實作為型別。

 變更所有對 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的呼叫，以傳遞這項（我在 Visual Basic 中）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當您使用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 來控制其他物件的存留期時，才會隱藏此規則的警告。 如果 <xref:System.IDisposable.Dispose%2A> 的執行不會呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>，請勿隱藏此規則的警告。 在此情況下，無法抑制完成會降低效能，且不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示不正確呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的方法。

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例顯示可正確呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的方法。

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>請參閱
 [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
