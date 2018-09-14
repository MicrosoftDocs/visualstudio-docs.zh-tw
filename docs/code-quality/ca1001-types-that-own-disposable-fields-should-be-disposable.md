---
title: CA1001：具有可處置欄位的類型應該是可處置的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a73acee1c01aba7a638d27c0e772e4fbf5e19384
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546931"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001：具有可處置欄位的類型應該是可處置的

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|類別|Microsoft.Design|
|中斷變更|非分行-如果類型不是組件外部可見。<br /><br /> 中斷-如果組件外部可見的型別。|

## <a name="cause"></a>原因
 類別會宣告及實作是執行個體欄位<xref:System.IDisposable?displayProperty=fullName>型別和該類別未實作<xref:System.IDisposable>。

## <a name="rule-description"></a>規則描述
 類別會實作<xref:System.IDisposable>處置 unmanaged 資源，其所擁有的介面。 是的執行個體欄位<xref:System.IDisposable>類型表示欄位擁有 unmanaged 的資源。 宣告的類別<xref:System.IDisposable>欄位間接擁有 unmanaged 的資源，且應實作<xref:System.IDisposable>介面。 如果類別未直接擁有任何 unmanaged 的資源，它應該不會實作完成項。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作<xref:System.IDisposable>進出<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法呼叫<xref:System.IDisposable.Dispose%2A>欄位的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類別和類別，藉由實作會滿足規則<xref:System.IDisposable>。 類別未實作完成項，因為類別並未直接擁有任何 unmanaged 的資源。

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049：具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)