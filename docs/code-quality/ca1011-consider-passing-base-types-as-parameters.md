---
title: CA1011：建議將基底類型當做參數傳遞
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5d44077dbe839fe6ce6b369f8d8b3b828bdb982a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549426"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011：建議將基底類型當做參數傳遞

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法宣告包含是衍生的類型，型式參數，此方法會呼叫只有參數的基底類型的成員。

## <a name="rule-description"></a>規則描述
 當方法宣告將基底類型指定為參數，則從此基底類型衍生的任何類型都可以當做對應引數傳遞給方法。 在方法主體內使用的引數時，會執行的特定方法取決於引數的類型。 如果不需要額外的功能所提供的衍生型別，則使用基底型別可讓更廣泛地運用此方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更參數的型別與其基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告

- 如果方法必須由衍生的型別所提供的特定功能

     \-或-

- 若要強制執行僅衍生的類型，或是衍生程度較大的類型，傳遞至方法。

 在這些情況下，程式碼會更穩固因為強式型別檢查的編譯器和執行階段所提供。

## <a name="example"></a>範例
 下列範例示範的方法中， `ManipulateFileStream`，可用於只使用<xref:System.IO.FileStream>違反此規則的物件。 第二個方法中， `ManipulateAnyStream`，來取代符合規則<xref:System.IO.FileStream>參數使用<xref:System.IO.Stream>。

 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1059：成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)