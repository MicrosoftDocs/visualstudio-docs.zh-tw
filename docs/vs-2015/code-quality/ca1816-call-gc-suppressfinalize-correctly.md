---
title: CA1816：呼叫 GC。SuppressFinalize 正確 |Microsoft Docs
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
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546766"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816:正確呼叫 GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|類別|Microsoft. 使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因

- 未呼叫的實作為的方法 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。

- 不是執行呼叫的方法 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。

- <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>在 Visual Basic) 中，方法會呼叫並傳遞此 (Me 以外的內容。

## <a name="rule-description"></a>規則描述
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法可讓使用者在物件變成可供垃圾收集之前，隨時釋放資源。 如果 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 呼叫方法，它會釋出物件的資源。 這會導致不必要的終止。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 應該呼叫， <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 讓垃圾收集行程不會呼叫物件的完成項。

 若要防止具有完成項的衍生類型必須重新執行 [IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) 並呼叫它，沒有完成項的未密封型別應該仍會呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規：

 如果方法是的實 <xref:System.IDisposable.Dispose%2A> ，請加入的呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。

 如果方法不是的實執行 <xref:System.IDisposable.Dispose%2A> ，請移除對的呼叫， <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 或將它移至類型的 <xref:System.IDisposable.Dispose%2A> 實作為。

 在 Visual Basic) 中，將所有的呼叫變更為 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ，以傳遞此 (Me。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您要 deliberating 使用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 來控制其他物件的存留期，則只會隱藏此規則的警告。 如果未呼叫的執行，請勿隱藏此規則的警告 <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。 在此情況下，無法抑制完成將會降低效能，而且不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示不正確呼叫的方法 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例會顯示正確呼叫的方法 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 。

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2215:Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216:可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>另請參閱
 [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
