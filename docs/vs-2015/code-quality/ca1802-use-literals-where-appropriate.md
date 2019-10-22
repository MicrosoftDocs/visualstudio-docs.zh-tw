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
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671520"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802：建議在適當時使用常值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 欄位會 `static` 和 `readonly` （在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中 `Shared` 和 `ReadOnly`）進行宣告，並使用在編譯時期可的值進行初始化。

## <a name="rule-description"></a>規則描述
 呼叫宣告類型的靜態構造函式時，會在執行時間計算 `static``readonly` 欄位的值。 如果 `static``readonly` 欄位在宣告時初始化，而且未明確宣告靜態的函式，則編譯器會發出靜態的函式來初始化欄位。

 @No__t_0 欄位的值會在編譯時期進行計算並儲存在中繼資料中，這會在與 `static``readonly` 欄位比較時，增加執行時間效能。

 因為指派給目標欄位的值是在編譯時期可，所以請將宣告變更為 `const` 欄位，以便在編譯時期（而不是在執行時間）計算該值。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請以 `const` 修飾詞取代 `static` 和 `readonly` 修飾詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告，或停用規則（如果效能不成問題）。

## <a name="example"></a>範例
 下列範例顯示的類型 `UseReadOnly`，其違反規則和符合規則的類型 `UseConstant`。

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
