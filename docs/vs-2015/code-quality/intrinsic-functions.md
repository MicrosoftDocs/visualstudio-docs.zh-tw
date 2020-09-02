---
title: 內建函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277956"
---
# <a name="intrinsic-functions"></a>內建函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SAL 中的運算式可以是 C/C++ 運算式 (假設該運算式沒有副作用的話)，例如 ++、-- 和函式呼叫在這個內容中全都有副作用。  但是 SAL 確實提供一些類似函式的物件，以及可在 SAL 運算式中使用的一些保留符號。 這些稱為 *內建函式*。  
  
## <a name="general-purpose"></a>一般用途  
 下列內建函式註釋提供 SAL 的一般公用程式。  
  
|Annotation|描述|  
|----------------|-----------------|  
|`_Curr_`|目前標註之物件的同義字。  正在使用 `_At_` 註釋時，`_Curr_` 和 `_At_` 的第一個參數相同。  否則，它會是與註釋在語彙上相關聯的參數或整個函式/傳回值。|  
|`_Inexpressible_(expr)`|表示緩衝區的大小太複雜而無法使用註釋運算式表示的情況，例如，透過掃描輸入資料集，然後計算所選取成員的方式計算。|  
|`_Nullterm_length_(param)`|`param` 這是緩衝區中最多（但不包括 null 結束字元）的元素數目。 它可以套用至非匯總、非 void 型別的任何緩衝區。|  
|`_Old_(expr)`|在前置條件下進行評估時，`_Old_` 會傳回輸入值 `expr`。  在後置條件下進行評估時，它會傳回值 `expr`，因為它已在前置條件下進行評估。|  
|`_Param_(n)`|`n`函數的第一個參數，從1算到 `n` ，而且 `n` 是常值整數常數。 如果參數名為，這個批註就會與依名稱存取參數相同。 **注意：** `n`可以參考省略號定義的位置參數，或可用於不使用名稱的函式原型。  |  
|`return`|C/c + + 保留關鍵字 `return` 可用於 SAL 運算式中，以表示函式的傳回值。  值只能在後置狀態下使用，因此在前置狀態下使用就是語法錯誤。|  
  
## <a name="string-specific"></a>字串特定  
 下列內建函式註釋可讓您操作字串。 這四種函式的目的都相同：傳回 null 結束字元之前所找到類型的項目數。 差異在於項目中參考的資料類型。 請注意，如果您要指定不是以字元組成之以 null 終止的緩衝區長度，請使用前一節中的 `_Nullterm_length_(param)` 註釋。  
  
|Annotation|描述|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` 這是字串中的元素數目，最多（但不包括 null 結束字元）。 這個注釋會保留給字串字元類型。|  
|`strlen(param)`|`param` 這是字串中的元素數目，最多（但不包括 null 結束字元）。 這個批註是保留供字元陣列使用，而且類似 C 執行時間函式 [strlen ( # B1 ](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)。|  
|`wcslen(param)`|`param` 這是字串中最多可 (但不包括) null 結束字元的元素數目。 此批註已保留供寬字元陣列使用，類似于 C 執行時間函式 [wcslen ( # B1 ](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/c + + 程式碼瑕疵](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [瞭解 SAL](../code-quality/understanding-sal.md)   
 [標注函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [標注函式行為](../code-quality/annotating-function-behavior.md)   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用注釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
