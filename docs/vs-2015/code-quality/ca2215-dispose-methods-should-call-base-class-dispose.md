---
title: CA2215： Dispose 方法應該呼叫基類處置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662856"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215：Dispose 方法應該呼叫基底類別處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 實 <xref:System.IDisposable?displayProperty=fullName> 的型別繼承自也會實 <xref:System.IDisposable> 的型別。 繼承類型的 <xref:System.IDisposable.Dispose%2A> 方法不會呼叫父類型的 <xref:System.IDisposable.Dispose%2A> 方法。

## <a name="rule-description"></a>規則描述
 如果類型繼承自可處置的類型，則必須從本身的 <xref:System.IDisposable.Dispose%2A> 方法中呼叫基底類型的 <xref:System.IDisposable.Dispose%2A> 方法。 呼叫基底類型方法 Dispose 可確保釋放基底類型所建立的任何資源。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請呼叫 `base`。<xref:System.IDisposable.Dispose%2A> 在您的 <xref:System.IDisposable.Dispose%2A> 方法中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果 `base` 的呼叫，則可以放心地隱藏此規則的警告。<xref:System.IDisposable.Dispose%2A> 在比規則檢查更深入的呼叫層級發生。

## <a name="example"></a>範例
 下列範例顯示的類型 `TypeA`，它會執行 <xref:System.IDisposable>。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示繼承自類型 `TypeA` 的類型 `TypeB`，並正確地呼叫其 <xref:System.IDisposable.Dispose%2A> 方法。

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>請參閱
 <xref:System.IDisposable?displayProperty=fullName>[處置模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
