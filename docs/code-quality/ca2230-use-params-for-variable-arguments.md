---
title: CA2230:必須使用 params 作為變數引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0639d30771b3a6bb288ddbf9644dda2efcd5f90d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231352"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230:必須使用 params 作為變數引數

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|分類|Microsoft.Usage|
|重大變更|中斷|

## <a name="cause"></a>原因
公用或受保護的類型包含使用`VarArgs`呼叫慣例的公用或受保護的方法。

## <a name="rule-description"></a>規則描述
`VarArgs`呼叫慣例會搭配採用可變數目參數的特定方法定義使用。 使用`VarArgs`呼叫慣例的方法不 Common Language Specification （CLS）相容，而且可能無法跨程式設計語言存取。

在C#中， `VarArgs`當方法的參數`__arglist`清單以關鍵字結尾時，會使用呼叫慣例。 Visual Basic 不支援`VarArgs`呼叫慣例，而且視覺效果C++只允許在使用橢圓形`...`標記法的非受控碼中使用。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正中C#此規則的違規情形，請使用[params](/dotnet/csharp/language-reference/keywords/params) `__arglist`關鍵字，而不是。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示兩個方法，其中一個會違反規則，另一個則符合規則。

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)