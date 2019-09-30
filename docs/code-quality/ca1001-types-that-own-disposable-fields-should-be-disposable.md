---
title: CA1001：具有可處置欄位的類型應該為可處置
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bda8fc80992a2246c30e28582eb93b4624ab81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236685"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001：具有可處置欄位的類型應該為可處置

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|分類|Microsoft.Design|
|重大變更|不中斷-如果在元件外部看不到此類型。<br /><br /> 中斷-如果類型在元件外部是可見的。|

## <a name="cause"></a>原因
類別會宣告並實作為<xref:System.IDisposable?displayProperty=fullName>類型的實例欄位，而類別不會執行。 <xref:System.IDisposable>

## <a name="rule-description"></a>規則描述
類別會執行<xref:System.IDisposable>介面來處置它所擁有的非受控資源。 屬於<xref:System.IDisposable>類型的實例欄位表示該欄位擁有非受控資源。 宣告<xref:System.IDisposable>欄位的類別會間接擁有非受控資源，而且應該會<xref:System.IDisposable>執行介面。 如果類別未直接擁有任何非受控資源，則不應執行完成項。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請<xref:System.IDisposable>在<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法中執行和， <xref:System.IDisposable.Dispose%2A>並呼叫欄位的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的類別，以及藉由執行<xref:System.IDisposable>來滿足規則的類別。 類別不會執行完成項，因為類別不會直接擁有任何非受控資源。

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>相關規則
[CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215Dispose 方法應該呼叫基類處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049:擁有原生資源的類型應該是可處置的](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)