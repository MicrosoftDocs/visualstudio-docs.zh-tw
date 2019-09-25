---
title: CA2214:不要呼叫建構函式中的可覆寫方法
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8eb881da0a7ed243bda35079f617a314053f2d85
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231293"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214:不要呼叫建構函式中的可覆寫方法

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

未密封類型的函式會呼叫其類別中定義的虛擬方法。

## <a name="rule-description"></a>規則描述

呼叫虛擬方法時，在執行時間之前，不會選取執行方法的實際類型。 當函式呼叫虛擬方法時，叫用方法之實例的函式可能尚未執行。

> [!NOTE]
> 此規則的舊版分析會有不同的 **\[診斷訊息「函式名稱」包含呼叫鏈，這會導致呼叫類別所定義的虛擬方法。請檢查下列呼叫堆疊是否有非**預期的結果」。 此規則的[FxCop 分析器](install-fxcop-analyzers.md)執行包含「**不要在函式中呼叫可覆寫的方法**」的診斷訊息。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請不要從類型的函式內呼叫類型的虛擬方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 應重新設計此函式，以排除對虛擬方法的呼叫。

## <a name="example"></a>範例

下列範例示範違反此規則的效果。 測試應用程式會建立的`DerivedType`實例，這會造成其基類（`BadlyConstructedType`）的執行程式。 `BadlyConstructedType`的函式不正確地呼叫`DoSomething`虛擬方法。 如輸出所示， `DerivedType.DoSomething()`會在`DerivedType`執行之前執行的函式。

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

這個範例會產生下列輸出：

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```