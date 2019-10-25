---
title: 全文檢索搜尋提示 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac683ff6e7079478d5b4e642918df4e281a53f0b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645658"
---
# <a name="full-text-search-tips"></a>全文檢索搜尋提示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [說明] 中尋找資訊的其中一個更有效方法是執行全文檢索搜尋。 若要縮小並自訂您的結果，您必須了解語法對查詢有何影響。 本主題提供秘訣、程序和詳細的語法資訊，以協助您更精心製作查詢。

## <a name="full-text-search-tips"></a>全文檢索搜尋提示
 如果您了解 [說明] 如何解譯您在查詢中使用的格式，您可以建立更具目標性的搜尋，只傳回有興趣的主題。 這些格式包括特殊字元、保留字和篩選。

### <a name="general-guidelines"></a>一般方針
 下表包含一些基本規則和指導方針，以便開發 [說明] 中的搜尋查詢。

|語法|說明|
|------------|-----------------|
|區分大小寫|搜尋不區分大小寫。 使用大寫或小寫字元開發您的搜尋準則。 例如，"OLE" 和 "ole" 傳回相同的結果。|
|字元組合|您無法只搜尋個別的字母 (a – z) 或數字 (0 – 9)。 如果您嘗試搜尋特定的保留字，例如 "and"、"from" 和 "with"，則會忽略它們。 如需詳細資訊，請參閱本主題稍後的「搜尋中忽略的字 (停用字詞)」。|
|評估順序|搜尋查詢會從左到右評估。|

### <a name="search-syntax"></a>搜尋語法
 如果您指定搜尋字串，其中包含多個單字，例如 "word1 word2"，該字串相當於輸入 "word1 AND word2"，它只會傳回包含搜尋字串中所有個別單字的主題。

> [!IMPORTANT]
> 1. 不支援片語搜尋。 如果您在搜尋字串中指定多個單字，傳回的主題會包含您指定的所有文字，但不一定是您指定的精確對應片語。
>    2. 使用邏輯運算子指定搜尋片語中文字之間的關聯性。 您可以包含邏輯運算子，例如 AND、OR、NOT 和 NEAR，以進一步精簡您的搜尋。 例如，如果您搜尋 "declaring NEAR union"，搜尋結果所包含的主題會包含 "declaring" 和 "union" 等字，且彼此之間相隔不超過幾個字。 如需詳細資訊，請參閱[搜尋運算式中的邏輯運算子](../ide/logical-operators-in-search-expressions.md)。

### <a name="filters"></a>篩選條件
 您可以使用進階搜尋運算子，進一步限制搜尋結果。 說明包含三個類別，可用來篩選全文檢索搜尋的結果︰標題、程式碼和關鍵字。 如需詳細資訊，請參閱[搜尋運算式中的進階搜尋運算子](../ide/advanced-search-operators-in-search-expressions.md)。

### <a name="ranking-of-search-results"></a>搜尋結果的等級
 搜尋演算法套用特定準則，以協助針對在結果清單中將搜尋結果評級為較高或較低。 一般情況下︰

1. 標題中包含搜尋文字之內容的等級會比不包含的內容高。

2. 包含非常接近搜尋文字之內容的等級會比不接近的內容高。

3. 包含較高密度的搜尋文字之內容的等級會搜尋文字密度較低的內容。

### <a name="words-ignored-in-searches-stop-words"></a>搜尋中忽略的字 (停用字詞)
 全文檢索搜尋期間會自動忽略常出現的文字或數字，這些有時稱為停用字詞。 例如，如果您搜尋片語 "pass through"，搜尋結果會顯示包含單字 "pass" 但不包含 "through" 的主題。

## <a name="see-also"></a>另請參閱
 [在搜尋運算式中尋找 ](../ide/locate-information.md) [Logical 運算子的資訊](../ide/logical-operators-in-search-expressions.md)
