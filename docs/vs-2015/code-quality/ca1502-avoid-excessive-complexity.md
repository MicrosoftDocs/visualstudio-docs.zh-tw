---
title: CA1502：避免過度複雜 |Microsoft Docs
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
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547832"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502:避免造成過度複雜的方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|類別|Microsoft。可維護性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法的迴圈複雜度過大。

## <a name="rule-description"></a>規則描述
 *圈複雜度*會測量透過方法的線性獨立路徑數目，這取決於條件式分支的數目和複雜度。 較低的圈複雜度通常表示容易瞭解、測試和維護的方法。 迴圈複雜度是從方法的控制流程圖來計算，並以下列方式提供：

 圈複雜度 = 邊緣數目-節點數目 + 1

 其中，節點代表邏輯分支點，而邊緣代表節點之間的線條。

 當圈複雜度大於25時，此規則會報告違規。

 您可以在[測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)中深入瞭解程式碼計量，

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請重構方法，以降低其圈複雜度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果無法輕易降低複雜性，而且方法很容易瞭解、測試和維護，就可以放心地隱藏此規則的警告。 特別的是，包含大型 `switch` （ `Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ）語句的方法是排除的候選項。 在開發週期中不穩定程式碼基底的風險，或在先前隨附的程式碼中引進執行時間行為的非預期變更，可能會超過重構程式碼的維護性優勢。

## <a name="how-cyclomatic-complexity-is-calculated"></a>如何計算圈複雜度
 迴圈複雜度的計算方式是將1新增至下列內容：

- 分支的數目（例如 `if` 、 `while` 和 `do` ）

- 中的 `case` 語句數目`switch`

  下列範例顯示迴圈複雜度不同的方法。

## <a name="example"></a>範例
 **1的圈複雜度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>範例
 **2的圈複雜度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>範例
 **圈複雜度為3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>範例
 **量的圈複雜度為8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>相關規則
 [CA1501:避免在物件間過度繼承](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>另請參閱
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
