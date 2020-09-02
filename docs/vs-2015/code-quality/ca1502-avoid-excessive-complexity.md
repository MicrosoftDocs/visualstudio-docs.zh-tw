---
title: CA1502：避免過度複雜性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547832"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502:避免造成過度複雜的方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|類別|Microsoft 的可維護性|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法的迴圈複雜度很高。

## <a name="rule-description"></a>規則描述
 迴圈*複雜度*會透過方法來測量以線性方式獨立的路徑數目，而此方法是由條件式分支的數目和複雜度所決定。 低圈複雜度通常表示很容易瞭解、測試和維護的方法。 迴圈複雜度是從方法的控制流程圖形計算而得，如下所示：

 迴圈複雜度 = 邊緣數目-節點數目 + 1

 其中節點代表邏輯分支點，而邊緣代表節點之間的線條。

 當圈複雜度超過25時，此規則會報告違規。

 您可以深入瞭解如何 [測量 Managed 程式碼的複雜性和可維護性的](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)程式碼計量，

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請重構方法以降低其圈複雜度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果無法輕易地降低複雜性，而且方法很容易瞭解、測試和維護，則可以放心隱藏此規則的警告。 尤其 `switch` 是在) 語句中包含大型 (的方法， `Select` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 是排除的候選項。 在開發週期中延遲不穩定程式碼基底的風險，或在先前隨附的程式碼中引進非預期的執行時間行為變更，可能會超過重構程式碼的可維護性優勢。

## <a name="how-cyclomatic-complexity-is-calculated"></a>如何計算圈複雜度
 迴圈複雜度的計算方式是將1新增至下列內容：

-  (的分支數目，例如 `if` 、 `while` 和 `do`) 

- 中的 `case` 語句數目 `switch`

  下列範例顯示具有不同迴圈複雜度的方法。

## <a name="example"></a>範例
 **迴圈複雜度為1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>範例
 **2的迴圈複雜度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>範例
 **迴圈複雜度為3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>範例
 **迴圈複雜度為8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>相關規則
 [CA1501:避免在物件間過度繼承](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>另請參閱
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
