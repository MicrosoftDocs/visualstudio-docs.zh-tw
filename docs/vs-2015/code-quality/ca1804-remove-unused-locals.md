---
title: CA1804 必須：移除未使用的區域變數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543880"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804:必須移除未使用的區域變數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|類別|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法會宣告區域變數，但不會使用變數，但可能是指派語句的收件者。 針對此規則的分析，必須以偵錯工具建立已測試的元件，且關聯的程式資料庫（.pdb）檔案必須可供使用。

## <a name="rule-description"></a>規則描述
 未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除或使用本機變數。 請注意，在啟用此選項時，所包含的 c # 編譯器會 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 移除未使用的區域變數 `optimize` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果變數是編譯器發出，則隱藏此規則的警告。 如果效能和程式碼維護不是主要考慮，也可以安全地隱藏此規則的警告，或停用規則。

## <a name="example"></a>範例
 下列範例顯示數個未使用的區域變數。

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1809:避免在方法中包含過多區域變數](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801:必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)
