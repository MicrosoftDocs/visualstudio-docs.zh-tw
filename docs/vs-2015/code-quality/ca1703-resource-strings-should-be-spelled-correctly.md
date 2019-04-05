---
title: CA1703:資源字串應該使用正確的拼字 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1ff5a2600a4f40673f7d38dfe551ab9ac8cfe29
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939929"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703:資源字串應該使用正確的拼字
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|分類|Microsoft.Naming|
|中斷變更|非重大|

## <a name="cause"></a>原因
 資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述
 此規則會將資源字串剖析成單字 （token 化的複合字），並檢查每個字/語彙基元的拼字。 如需剖析演算法的詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

 預設情況下，會使用英文 (en) 版本的拼字檢查程式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，使用完整的文字拼寫正確，或將文字加入自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 正確拼寫的字會減少所需了解新的軟體程式庫的時間。

## <a name="related-rules"></a>相關的規則
 [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204:常值應該使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
