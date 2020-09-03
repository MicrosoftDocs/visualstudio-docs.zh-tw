---
title: CA2204：常值應正確拼寫 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546272"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204:常值必須使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法會將常值字串傳遞給在需要當地語系化字串的參數或屬性中使用，而常值字串包含一或多個 Microsoft 拼寫檢查庫無法辨識的字詞。

## <a name="rule-description"></a>規則描述
 當下列一或多個情況成立時，此規則會檢查傳遞做為值的常值字串至參數或屬性：

- <xref:System.ComponentModel.LocalizableAttribute>參數或屬性的屬性設定為 true。

- 參數或屬性名稱包含「文字」、「訊息」或「標題」。

- 傳遞至主控台的字串參數名稱。 WriteLine 方法為 "value" 或 "format"。

  此規則會將常值字串剖析為單字、token 化複合單字，並檢查每個單字/token 的拼寫。 如需剖析演算法的詳細資訊，請參閱 [CA1704：識別碼應該拼寫正確](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

  根據預設，會使用拼寫檢查程式的英文 (en) 版本。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正單字的拼寫，或將文字加入自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 拼寫正確的單字可減少新軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關規則
 [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
