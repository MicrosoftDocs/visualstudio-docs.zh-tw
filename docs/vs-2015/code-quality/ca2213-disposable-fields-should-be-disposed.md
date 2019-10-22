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
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662889"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213：可處置的欄位應該受到處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 執行 <xref:System.IDisposable?displayProperty=fullName> 的類型會宣告也會實作為 <xref:System.IDisposable> 之類型的欄位。 宣告類型的 <xref:System.IDisposable.Dispose%2A> 方法不會呼叫欄位的 <xref:System.IDisposable.Dispose%2A> 方法。

## <a name="rule-description"></a>規則描述
 「類型」負責處置其所有非受控資源;這是藉由執行 <xref:System.IDisposable> 來完成。 此規則會檢查可處置的類型是否 `T` 宣告屬於可處置類型之實例的欄位 `F` `FT`。 針對每個欄位 `F`，此規則會嘗試找出對 `FT.Dispose` 的呼叫。 此規則會搜尋 `T.Dispose` 所呼叫的方法，其中一個層級較低（由 `FT.Dispose` 所呼叫之方法所呼叫的方法）。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請在執行 <xref:System.IDisposable> 類型的欄位上呼叫 <xref:System.IDisposable.Dispose%2A>，如果您負責配置和釋放欄位所保留的非受控資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不負責釋放欄位所持有的資源，或呼叫 <xref:System.IDisposable.Dispose%2A> 在比規則檢查更深入的呼叫層級時，就可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的型別 `TypeA` 會執行 <xref:System.IDisposable> （在先前的討論中 `FT`）。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別 `TypeB`，方法是將欄位 `aFieldOfADisposableType` （在上一個討論中 `F`）宣告為可處置的型別（`TypeA`），而不是在欄位上呼叫 <xref:System.IDisposable.Dispose%2A>。 `TypeB` 對應到先前討論中的 `T`。

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>請參閱
 <xref:System.IDisposable?displayProperty=fullName>[處置模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
