---
title: CA2213：應處置可處置的欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534572"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213:可處置的欄位應該受到處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 一個型別，它 <xref:System.IDisposable?displayProperty=fullName> 會宣告也會實作為類型的欄位 <xref:System.IDisposable> 。 宣告 <xref:System.IDisposable.Dispose%2A> 類型的方法不會呼叫欄位的方法 <xref:System.IDisposable.Dispose%2A> 。

## <a name="rule-description"></a>規則描述
 「類型」負責處置其所有非受控資源;這是藉由執行來完成 <xref:System.IDisposable> 。 此規則會檢查可處置的類型是否宣告的 `T` 欄位 `F` 是可處置類型的實例 `FT` 。 針對每個欄位 `F` ，規則會嘗試找出對的呼叫 `FT.Dispose` 。 此規則會搜尋所呼叫的方法 `T.Dispose` ，以及一個層級較低的（由呼叫的方法所呼叫的方法 `FT.Dispose` ）。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請 <xref:System.IDisposable.Dispose%2A> 在執行類型的欄位上呼叫， <xref:System.IDisposable> 如果您負責配置和釋放欄位所保留的非受控資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不負責釋放欄位所持有的資源，或呼叫 <xref:System.IDisposable.Dispose%2A> 發生在比規則檢查更深入的呼叫層級，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的型別 `TypeA` 會執行 <xref:System.IDisposable> （ `FT` 在先前的討論中）。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示 `TypeB` 違反此規則的類型，方法是將欄位 `aFieldOfADisposableType` （ `F` 在先前的討論中）宣告為可處置的類型（ `TypeA` ），而不是 <xref:System.IDisposable.Dispose%2A> 在欄位上呼叫。 `TypeB`對應于 `T` 先前討論中的。

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName>[Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
