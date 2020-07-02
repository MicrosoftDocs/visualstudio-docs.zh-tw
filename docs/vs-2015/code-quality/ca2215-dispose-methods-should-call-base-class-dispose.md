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
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534377"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215:Dispose 方法應該呼叫基底類別處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 執行的類型會 <xref:System.IDisposable?displayProperty=fullName> 繼承自也會執行的類型 <xref:System.IDisposable> 。 <xref:System.IDisposable.Dispose%2A>繼承類型的方法不會呼叫 <xref:System.IDisposable.Dispose%2A> 父類型的方法。

## <a name="rule-description"></a>規則描述
 如果類型繼承自可處置的類型，則必須 <xref:System.IDisposable.Dispose%2A> 從本身的方法中呼叫基底類型的方法 <xref:System.IDisposable.Dispose%2A> 。 呼叫基底類型方法 Dispose 可確保釋放基底類型所建立的任何資源。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請呼叫 `base` 。<xref:System.IDisposable.Dispose%2A> 在您的 <xref:System.IDisposable.Dispose%2A> 方法中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果呼叫，則可以安全地隱藏此規則的警告 `base` 。<xref:System.IDisposable.Dispose%2A> 在比規則檢查更深入的呼叫層級發生。

## <a name="example"></a>範例
 下列範例顯示的型別 `TypeA` 會執行 <xref:System.IDisposable> 。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示 `TypeB` 繼承自類型的類型 `TypeA` ，並正確地呼叫其 <xref:System.IDisposable.Dispose%2A> 方法。

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName>[Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
