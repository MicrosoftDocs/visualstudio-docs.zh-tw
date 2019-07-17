---
title: CA2204:常值應該使用正確的拼字 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a08cb7cee2af51ade4b94dbf675ff83d7da456e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142515"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204:常值必須使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 常值字串，用於參數或需要的當地語系化的字串和常值字串屬性，方法傳遞包含一或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述
 此規則會檢查常值字串做為值傳遞至參數或屬性，當一或多個下列情況為 true:

- <xref:System.ComponentModel.LocalizableAttribute>參數或屬性的屬性設定為 true。

- 參數或屬性名稱中包含 「 文字 」、 「 訊息 」，或 「 標題 」。

- 「 值 」 或"format"字串參數傳遞至 Console.Write 或 Console.WriteLine 方法的名稱。

  此規則會將常值字串剖析成單字、 token 化複合字，並檢查每個字/語彙基元的拼字。 如需剖析演算法的詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

  預設情況下，會使用英文 (en) 版本的拼字檢查程式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，更正這個字的拼字，或將該字加入至自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱[How to:自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 正確拼寫的字會減少新的軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關的規則
 [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
