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
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231166"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220:完成項應該呼叫基底類別完成項

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

覆寫<xref:System.Object.Finalize%2A?displayProperty=fullName>的類型不會呼叫其<xref:System.Object.Finalize%2A>基類中的方法。

## <a name="rule-description"></a>規則描述

最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保這一點，類型必須從其<xref:System.Object.Finalize%2A>本身<xref:System.Object.Finalize%2A>的方法中呼叫其基類方法。 C#編譯器會自動新增對基類完成項的呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請從您<xref:System.Object.Finalize%2A> <xref:System.Object.Finalize%2A>的方法呼叫基底類型的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 某些以通用語言執行平臺為目標的編譯器會將基底類型的完成項呼叫插入 Microsoft 中繼語言（MSIL）。 如果報告來自此規則的警告，則您的編譯器不會插入呼叫，而且您必須將它新增至您的程式碼。

## <a name="example"></a>範例

下列 Visual Basic 範例顯示在其基類`TypeB`中正確<xref:System.Object.Finalize%2A>呼叫方法的類型。

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>另請參閱

- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)