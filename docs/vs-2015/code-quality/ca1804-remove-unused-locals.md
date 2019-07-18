---
title: CA1804:移除未使用的區域變數 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38fe76bbdf2fdafa69ca12caf4f131a05f783954
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143122"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804:必須移除未使用的區域變數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法的本機變數宣告，但未使用的變數，但可能收件者在指派陳述式。 此規則的分析，請測試的組件必須以偵錯資訊建置，並必須可以使用相關聯的程式資料庫 (.pdb) 檔案。

## <a name="rule-description"></a>規則描述
 未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除，或使用本機變數。 請注意，C# 編譯器隨附[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]移除未使用的本機變數時`optimize`啟用選項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果變數是由編譯器發出，則隱藏此規則的警告。 也很安全隱藏這項規則的警告，或停用規則，如果效能和程式碼維護不是主要的考量。

## <a name="example"></a>範例
 下列範例會示範幾個未使用的本機變數。

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1809:避免過多區域變數](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801： 必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)
