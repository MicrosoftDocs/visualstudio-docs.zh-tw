---
title: CA2241 必須：為格式化方法提供正確的引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1dfd770efd4d690930155d2486b8ff1859065272
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543646"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241:必須提供格式化方法的正確引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 `format`傳遞給方法（例如、或）的字串引數 <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> <xref:System.String.Format%2A?displayProperty=fullName> 不包含對應至每個物件引數的格式專案，反之亦然。

## <a name="rule-description"></a>規則描述
 方法的引數（例如 <xref:System.Console.WriteLine%2A> 、 <xref:System.Console.Write%2A> 和） <xref:System.String.Format%2A> 包含後面接著數個實例的格式字串 <xref:System.Object?displayProperty=fullName> 。 格式字串是由表單 {index [，align] [：格式為]} 的文字和內嵌格式專案所組成。 'index' 是以零起始的整數，會指出需要格式化的物件。 如果物件在格式字串中沒有對應的索引，則會忽略該物件。 如果 ' index ' 所指定的物件不存在， <xref:System.FormatException?displayProperty=fullName> 就會在執行時間擲回。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請為每個物件引數提供格式專案，並為每個格式專案提供物件引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個規則違規。

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
