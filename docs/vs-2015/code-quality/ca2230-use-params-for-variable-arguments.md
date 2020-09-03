---
title: CA2230 必須：對變數引數使用 params |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540357"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230:必須使用 params 作為變數引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|類別|Microsoft. 使用量|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的型別包含使用呼叫慣例的公用或受保護的方法 `VarArgs` 。

## <a name="rule-description"></a>規則描述
 `VarArgs`呼叫慣例會搭配採用可變數參數數目的特定方法定義使用。 使用 `VarArgs` 呼叫慣例的方法不 Common Language Specification (CLS) 符合規範，而且可能無法跨程式設計語言進行存取。

 在 c # 中， `VarArgs` 當方法的參數清單以關鍵字結束時，會使用呼叫慣例 `__arglist` 。 Visual Basic 不支援 `VarArgs` 呼叫慣例，而且 Visual C++ 只允許在使用橢圓形標記法的非受控程式碼中使用 `...` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要在 c # 中修正此規則的違規情形，請使用 [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) 關鍵字取代 `__arglist` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個方法，一個違反規則，另一個符合規則。

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[語言獨立性和與語言無關的元件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
