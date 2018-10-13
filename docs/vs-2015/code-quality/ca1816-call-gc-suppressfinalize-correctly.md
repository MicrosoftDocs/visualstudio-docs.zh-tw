---
title: CA1816： 呼叫 GC。SuppressFinalize 正確 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 85e4a3f5d4f1fc3f326b79ec26d95a66c75b431d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213244"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816：正確呼叫 GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|分類|Microsoft。 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因

-   是的實作方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

-   不是實作的方法<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

-   方法會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>並傳遞非 this (Me Visual Basic 中)。

## <a name="rule-description"></a>規則描述
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法可讓使用者在任何階段變成可供記憶體回收的物件之前釋出資源。 如果<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>呼叫方法，它會釋出資源的物件。 這可讓完成項不必要。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>讓記憶體回收行程不會呼叫物件的完成項。

 若要避免使用完成項的衍生型別不必重新實作 [System.IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->)，若要呼叫它，而不需要完成項的非密封的類型仍應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形：

 如果方法是實作<xref:System.IDisposable.Dispose%2A>，將呼叫加入<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

 如果方法不是實作<xref:System.IDisposable.Dispose%2A>，移除對<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>或將它移到別的<xref:System.IDisposable.Dispose%2A>實作。

 變更所有呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>傳遞此 （我在 Visual Basic 中）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您 deliberating 使用，只能隱藏此規則的警告<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>控制其他物件的存留期。 請勿隱藏此規則的警告，如果實作<xref:System.IDisposable.Dispose%2A>不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。 在此情況下，無法隱藏最終化會降低效能，並不提供任何好處。

## <a name="example"></a>範例
 下列範例示範的方法，不正確地呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例示範的方法也正確地呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>另請參閱
 [Dispose 模式](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



