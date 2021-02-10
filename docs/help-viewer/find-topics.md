---
title: 搜尋主題 (說明檢視器)
description: 瞭解如何搜尋 Microsoft Help Viewer 中的主題。 使用萬用字元運算式、邏輯運算子和 advanced search 運算子自訂搜尋。
ms.date: 11/02/2017
ms.topic: how-to
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4ebf3bbd1fe04b13f31de7ebd8c513de670dd480
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944130"
---
# <a name="how-to-search-for-topics"></a>如何：搜尋主題

您可以使用全文檢索搜尋功能尋找包含的特定字詞的任何主題。 您也可以使用萬用字元運算式、邏輯運算子和進階的搜尋運算子來修改和自訂查詢。

若要開啟 **[搜尋] 索引** 標籤，請選擇 [說明 **檢視器**] 視窗中的 [**搜尋] 索引** 標籤，或者，如果您是鍵盤使用者，請選擇 **Ctrl** + **E**。

## <a name="to-perform-a-full-text-search"></a>執行全文檢索搜尋

1. 在搜尋方塊中，輸入您要尋找的文字。

2. 在搜尋查詢中，指定要套用至搜尋的邏輯或進階搜尋運算子 (如果有的話)。 若要搜尋所有可用的說明，請不要使用運算子。

    > [!NOTE]
    > 在[檢視器選項] 對話方塊中，如果您的主要地區設定不是英文，您可以指定其他喜好設定，例如要一次顯示的搜尋結果數目上限以及是否要包括英文內容。

3. 選擇 **Enter** 鍵。

     搜尋預設會傳回最多 200 個點閱數，並將其顯示在搜尋結果區域中。 每個結果的其他版本資訊可能會根據內容出現。

4. 若要檢視主題，請從結果清單中選擇其標題。

## <a name="full-text-search-tips"></a>全文檢索搜尋提示

如果您了解語法影響查詢的方式，則可以建立更具目標性的搜尋，只傳回有興趣的主題。 這些語法包括特殊字元、保留字和篩選條件。 本主題提供秘訣、程序和詳細的語法資訊，以協助您更精心製作查詢。

### <a name="general-guidelines"></a>一般指導方針

下表包含一些基本規則和指導方針，以便開發 [說明] 中的搜尋查詢。

|語法|描述|
|------------|-----------------|
|區分大小寫|搜尋不區分大小寫。 使用大寫或小寫字元開發您的搜尋準則。 例如，"OLE" 和 "ole" 傳回相同的結果。|
|字元組合|您無法只搜尋個別的字母 (a-z) 或數字 (0-9)。 如果您嘗試搜尋特定的保留字，例如 "and"、"from" 和 "with"，則會忽略它們。 如需詳細資訊，請參閱本主題稍後的[搜尋中忽略的字詞](#stopwords)。|
|評估順序|搜尋查詢會從左到右評估。|

### <a name="search-syntax"></a>搜尋語法

如果您指定搜尋字串，其中包含多個單字，例如 "word1 word2"，該字串相當於輸入 "word1 AND word2"，它只會傳回包含搜尋字串中所有個別單字的主題。

> [!IMPORTANT]
> - 不支援片語搜尋。 如果您在搜尋字串中指定多個單字，傳回的主題會包含您指定的所有文字，但不一定是您指定的精確對應片語。
> - 使用邏輯運算子指定搜尋片語中文字之間的關聯性。 您可以包含邏輯運算子，例如 AND、OR、NOT 和 NEAR，以進一步精簡您的搜尋。 例如，如果您搜尋 "declaring NEAR union"，搜尋結果所包含的主題會包含 "declaring" 和 "union" 等字，且彼此之間相隔不超過幾個字。 如需詳細資訊，請參閱[搜尋運算式中的邏輯運算子](../help-viewer/logical-operators-search-expressions.md)。

### <a name="filters"></a>篩選器

您可以使用進階搜尋運算子，進一步限制搜尋結果。 說明包含三個類別，可用來篩選全文檢索搜尋的結果︰標題、程式碼和關鍵字。

### <a name="ranking-of-search-results"></a>搜尋結果的等級

搜尋演算法套用特定準則，以協助針對在結果清單中將搜尋結果評級為較高或較低。 一般而言：

1. 標題中包含搜尋文字之內容的等級會比不包含的內容高。

2. 包含非常接近搜尋文字之內容的等級會比不接近的內容高。

3. 包含較高密度的搜尋文字之內容的等級會搜尋文字密度較低的內容。

### <a name=""></a><a name="stopwords"> 搜尋中忽略的字詞 (停用字詞) </a>

全文檢索搜尋期間會自動忽略常出現的文字或數字，這些有時稱為停用字詞。 例如，如果您搜尋片語 "pass through"，搜尋結果會顯示包含單字 "pass" 但不包含 "through" 的主題。

## <a name="see-also"></a>另請參閱

- [邏輯與進階運算子](../help-viewer/logical-operators-search-expressions.md)
- [如何：在索引中尋找主題](../help-viewer/find-topics-index.md)
- [如何：在目錄中尋找主題](../help-viewer/find-topics-toc.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)