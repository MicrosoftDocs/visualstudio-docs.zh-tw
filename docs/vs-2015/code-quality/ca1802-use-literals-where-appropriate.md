---
title: CA1802 建議：適當時使用常值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544400"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802:建議在適當時使用常值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|類別|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 欄位已宣告 `static` 和 `readonly` （ `Shared` 和中的 `ReadOnly` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ），並使用在編譯時期可的值進行初始化。

## <a name="rule-description"></a>規則描述
 呼叫宣告類型的 `static``readonly` 靜態函式時，會在執行時間計算欄位的值。 如果欄位在宣告 `static``readonly` 時初始化，而且未明確宣告靜態的函式，則編譯器會發出靜態的函式來初始化欄位。

 欄位的值 `const` 會在編譯時期計算並儲存在中繼資料中，這會在與欄位比較時增加執行時間效能 `static``readonly` 。

 因為指派給目標欄位的值是在編譯時期可，所以請將宣告變更為 `const` 欄位，以便在編譯時期（而不是在執行時間）計算該值。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以修飾詞取代 `static` 和 `readonly` 修飾詞 `const` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告，或停用規則（如果效能不成問題）。

## <a name="example"></a>範例
 下列範例顯示的類型 `UseReadOnly` 違反規則，以及 `UseConstant` 符合規則的類型。

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
