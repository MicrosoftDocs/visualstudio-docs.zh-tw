---
title: Ca2241： 必須提供格式化方法的正確引數 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d66e6c8efed7847420a4abc1773a9514ef44074f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884936"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241：必須提供格式化方法的正確引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 `format`字串引數傳遞至方法，例如<xref:System.Console.WriteLine%2A>， <xref:System.Console.Write%2A>，或<xref:System.String.Format%2A?displayProperty=fullName>不包含對應至每個物件引數，或反之亦然的格式項目。

## <a name="rule-description"></a>規則描述
 這類方法的引數<xref:System.Console.WriteLine%2A>， <xref:System.Console.Write%2A>，並<xref:System.String.Format%2A>包含格式字串，後面接著數個<xref:System.Object?displayProperty=fullName>執行個體。 格式字串所組成的文字和內嵌的格式項目表單的 {索引 [，對齊] [: formatString]}。 'index' 是以零起始的整數，會指出需要格式化的物件。 如果物件在格式字串中沒有對應的索引，則會忽略的物件。 'Index' 所指定的物件不存在，如果<xref:System.FormatException?displayProperty=fullName>會在執行階段擲回。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，每個物件引數提供的格式項目，並提供每個格式項目之物件引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個違反規則。

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]



