---
title: CA1001 具有：擁有可處置欄位的類型應該可以處置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42d21eb0bf32b3abb0eb26d3723123bf085914ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646321"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001：具有可處置欄位的類型應該是可處置的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft. Design|
|中斷變更|不中斷-如果在元件外部看不到此類型。<br /><br /> 中斷-如果類型在元件外部是可見的。|

## <a name="cause"></a>原因
 類別會宣告並實作為 <xref:System.IDisposable?displayProperty=fullName> 類型的實例欄位，而類別不會執行 <xref:System.IDisposable>。

## <a name="rule-description"></a>規則描述
 類別會執行 <xref:System.IDisposable> 介面，以處置它所擁有的非受控資源。 屬於 <xref:System.IDisposable> 類型的實例欄位，表示該欄位擁有非受控資源。 宣告 <xref:System.IDisposable> 欄位的類別會間接擁有非受控資源，而且應該會執行 <xref:System.IDisposable> 介面。 如果類別未直接擁有任何非受控資源，則不應執行完成項。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請執行 <xref:System.IDisposable>，並從 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法呼叫欄位的 <xref:System.IDisposable.Dispose%2A> 方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類別，以及藉由執行 <xref:System.IDisposable> 來滿足規則的類別。 類別不會執行完成項，因為類別不會直接擁有任何非受控資源。

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049：具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
