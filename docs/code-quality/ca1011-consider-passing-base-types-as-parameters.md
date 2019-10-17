---
title: CA1011：建議將基底類型當做參數傳遞
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fbb807f7146c781d2b97cf80f2e78c8beb5c38b4
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441665"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011：建議將基底類型當做參數傳遞

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|分類|Microsoft. Design|
|重大變更|中斷|

## <a name="cause"></a>原因

方法宣告包含屬於衍生類型的型式參數，而方法只會呼叫參數基底類型的成員。

## <a name="rule-description"></a>規則描述

當方法宣告將基底類型指定為參數，則從此基底類型衍生的任何類型都可以當做對應引數傳遞給方法。 在方法主體內使用引數時，所執行的特定方法會視引數的類型而定。 如果不需要衍生類型所提供的其他功能，則使用基底類型可更廣泛地使用方法。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將參數的類型變更為其基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

隱藏此規則的警告是安全的

- 如果方法需要衍生類型所提供的特定功能

     \-或-

- 若要強制只將衍生的型別或衍生的型別傳遞給方法。

在這些情況下，因為編譯器和執行時間所提供的強型別檢查，所以程式碼會更健全。

## <a name="example"></a>範例

下列範例顯示的方法 `ManipulateFileStream`，只能搭配 @no__t 1 物件使用，這會違反此規則。 第二個方法 `ManipulateAnyStream`，藉由使用 <xref:System.IO.Stream> 來取代 <xref:System.IO.FileStream> 參數，以滿足規則。

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>相關規則

[CA1059：成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
