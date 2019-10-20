---
title: CA2204：常值的拼寫應該正確 |Microsoft Docs
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
ms.openlocfilehash: d3e94f308936f898e555b1ad38e6a9d50051a276
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659544"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204：常值必須使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法會將常值字串傳遞至，其會在需要當地語系化字串的參數或屬性中使用，而且常值字串包含一個或多個 Microsoft 拼寫檢查程式庫無法辨識的文字。

## <a name="rule-description"></a>規則描述
 當下列一或多個情況成立時，此規則會檢查當做值傳遞給參數或屬性的常值字串：

- 參數或屬性的 <xref:System.ComponentModel.LocalizableAttribute> 屬性設定為 true。

- 參數或屬性名稱包含 "Text"、"Message" 或 "Caption"。

- 傳遞至主控台的字串參數名稱。 Write 或 Console。 WriteLine 方法可以是 "value" 或 "format"。

  此規則會將常值字串剖析成單字、token 化複合字組，並檢查每個單字/token 的拼寫。 如需剖析演算法的詳細資訊，請參閱[CA1704：識別碼應該正確拼寫](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

  根據預設，會使用拼寫檢查的英文（en）版本。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正單字的拼寫，或將此單字加入自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱[如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 拼寫正確的文字會減少新軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關規則
 [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
