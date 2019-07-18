---
title: CA2220:完成項應該呼叫基底類別完成項
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 034f80c9198ab098070e6642f4a4d96cff1744c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541854"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220:完成項應該呼叫基底類別完成項

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

一種類型，會覆寫<xref:System.Object.Finalize%2A?displayProperty=fullName>不會呼叫<xref:System.Object.Finalize%2A>其基底類別中的方法。

## <a name="rule-description"></a>規則描述

最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保此行為，類型必須呼叫其基底類別<xref:System.Object.Finalize%2A>方法內自己<xref:System.Object.Finalize%2A>方法。 C# 編譯器會自動新增至基底類別完成項呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，呼叫基底型別的<xref:System.Object.Finalize%2A>方法，從您<xref:System.Object.Finalize%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 某些以 common language runtime 為目標的編譯器插入的 Microsoft intermediate language (MSIL) 的基底型別的完成項呼叫。 如果報告此規則的警告，編譯器不會插入呼叫，以及您必須將它加入您的程式碼。

## <a name="example"></a>範例

下列 Visual Basic 範例會顯示為型別`TypeB`正確呼叫<xref:System.Object.Finalize%2A>其基底類別中的方法。

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>另請參閱

- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)