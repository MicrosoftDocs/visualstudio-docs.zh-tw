---
title: CA1703：資源字串應該拼寫正確 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9574ff022e0d5407b2683e5ba7a6b2e0cde5201e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669228"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703：資源字串應該拼寫正確
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft. 命名|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述
 此規則會將資源字串剖析成單字（token 化的複合字組），並檢查每個單字/token 的拼寫。 如需剖析演算法的詳細資訊，請參閱[CA1704：識別碼應該正確拼寫](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

 根據預設，會使用拼寫檢查的英文（en）版本。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用正確拼寫的完整單字，或將單字加入自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱[CA1704：識別碼應該正確拼寫](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 拼寫正確的文字會減少學習新軟體程式庫所需的時間。

## <a name="related-rules"></a>相關規則
 [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
