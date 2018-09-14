---
title: CA1026：不應使用預設參數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faced51a807a69ecc2e11a04e9ed5e292f4d3a19
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547603"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026：不應使用預設參數
|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的型別包含外部可見的方法，會使用預設參數。

## <a name="rule-description"></a>規則描述
 在 Common Language Specification (CLS); 允許使用預設參數的方法不過，CLS 允許編譯器忽略指派給這些參數的值。 忽略預設參數值的編譯器撰寫的程式碼必須明確地提供每個預設參數的引數。 若要維持您想要在程式語言之間的行為，使用預設參數的方法應該取代提供的預設參數的方法多載。

 編譯器會管理延伸模組，c + + 忽略預設參數的值，存取 managed 程式碼時也一樣。 Visual Basic 編譯器支援已使用的預設參數的方法[選擇性](/dotnet/visual-basic/language-reference/modifiers/optional)關鍵字。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，取代預設參數會使用提供的預設參數的方法多載的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示使用預設參數的方法，並提供對等功能的多載的方法。

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1025：必須以參數陣列取代重複的引數](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>另請參閱
 [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)