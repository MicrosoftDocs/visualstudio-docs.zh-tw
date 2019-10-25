---
title: 內建函式
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 4824cba4de67ad199974f5844c7f220a6fd6accc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745904"
---
# <a name="intrinsic-functions"></a>內建函式
SAL 中的運算式可以是 C/C++ 運算式 (假設該運算式沒有副作用的話)，例如 ++、-- 和函式呼叫在這個內容中全都有副作用。  不過，SAL 會提供一些類似函式的物件，以及一些可在 SAL 運算式中使用的保留符號。 這些稱為*內建函式*。

## <a name="general-purpose"></a>一般用途
下列內建函式註釋提供 SAL 的一般公用程式。

|註釋|描述|
|----------------|-----------------|
|`_Curr_`|目前標註之物件的同義字。  正在使用 `_At_` 註釋時，`_Curr_` 和 `_At_` 的第一個參數相同。  否則，它會是與註釋在語彙上相關聯的參數或整個函式/傳回值。|
|`_Inexpressible_(expr)`|表示緩衝區的大小太複雜而無法使用註釋運算式表示的情況，例如，透過掃描輸入資料集，然後計算所選取成員的方式計算。|
|`_Nullterm_length_(param)`|`param` 是緩衝區中最多但不包括 null 結束字元的元素數目。 它可以套用至非匯總、非 void 類型的任何緩衝區。|
|`_Old_(expr)`|在前置條件下進行評估時，`_Old_` 會傳回輸入值 `expr`。  在後置條件下進行評估時，它會傳回值 `expr`，因為它已在前置條件下進行評估。|
|`_Param_(n)`|函式的 `n`th 參數，計算從1到 `n`，而 `n` 是常值整數常數。 如果參數名為，則此注釋與依名稱存取參數的方式相同。 **注意：**  `n` 可能會參考由省略號定義的位置參數，或可用於不使用名稱的函式原型中。|
|`return`|您可以在C++ SAL 運算式中使用 C/reserved 關鍵字 `return` 來表示函數的傳回值。  值只能在後置狀態下使用，因此在前置狀態下使用就是語法錯誤。|

## <a name="string-specific"></a>特定字串
下列內建函式註釋可讓您操作字串。 這四種函式的目的都相同：傳回 null 結束字元之前所找到類型的項目數。 差異在於項目中參考的資料類型。 請注意，如果您要指定不是以字元組成之以 null 終止的緩衝區長度，請使用前一節中的 `_Nullterm_length_(param)` 註釋。

|註釋|描述|
|----------------|-----------------|
|`_String_length_(param)`|`param` 是字串中最多但不包括 null 結束字元的元素數目。 此批註會保留給字元字串類型。|
|`strlen(param)`|`param` 是字串中最多但不包括 null 結束字元的元素數目。 此注釋會保留供字元陣列使用，而且類似 C 執行時間函式[strlen （）](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)。|
|`wcslen(param)`|`param` 是字串中最多（但不包括） null 結束字元的元素數目。 這個批註已保留供寬字元陣列使用，而且類似 C 執行時間函式[wcslen （）](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)。|

## <a name="see-also"></a>請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
