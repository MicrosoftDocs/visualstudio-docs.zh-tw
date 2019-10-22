---
title: CA2230 必須：將 params 用於變數引數 |Microsoft Docs
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
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662835"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230：必須使用 params 做為變數引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft。使用方式|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含使用 `VarArgs` 呼叫慣例的公用或受保護的方法。

## <a name="rule-description"></a>規則描述
 @No__t_0 呼叫慣例會與接受可變數目參數的特定方法定義搭配使用。 使用 `VarArgs` 呼叫慣例的方法不符合 Common Language Specification （CLS）規範，而且可能無法跨程式設計語言存取。

 在C#中，當方法的參數清單以 `__arglist` 關鍵字結尾時，會使用 `VarArgs` 呼叫慣例。 Visual Basic 不支援 `VarArgs` 呼叫慣例，而且視覺效果C++只允許在使用省略號 `...` 標記法的非受控碼中使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正中C#此規則的違規情形，請使用[params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012)關鍵字，而不是 `__arglist`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個方法，其中一個會違反規則，另一個則符合規則。

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>請參閱
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[語言獨立性和與語言無關的元件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
