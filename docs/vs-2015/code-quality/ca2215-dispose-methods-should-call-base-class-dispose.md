---
title: 'CA2215: Dispose 方法應該呼叫基底類別處置 |Microsoft Docs'
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
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9115e661b5bd38a23e1429d545d29725a164069a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296877"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215：Dispose 方法應該呼叫基底類別處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別可實作<xref:System.IDisposable?displayProperty=fullName>繼承自型別同時實作<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>繼承類型的方法不會呼叫<xref:System.IDisposable.Dispose%2A>父類型的方法。

## <a name="rule-description"></a>規則描述
 如果類型繼承自可處置的類型，它必須呼叫<xref:System.IDisposable.Dispose%2A>方法，從其本身內的基底型別<xref:System.IDisposable.Dispose%2A>方法。 呼叫基底型別方法處置可確保會釋放基底型別所建立的任何資源。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫`base`。<xref:System.IDisposable.Dispose%2A> 在您<xref:System.IDisposable.Dispose%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果呼叫`base`。<xref:System.IDisposable.Dispose%2A> 就會發生更深層級呼叫比規則檢查。

## <a name="example"></a>範例
 下列範例顯示型別`TypeA`實作<xref:System.IDisposable>。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示型別`TypeB`繼承自型別`TypeA`，並正確地呼叫其<xref:System.IDisposable.Dispose%2A>方法。

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName> [處置模式](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



