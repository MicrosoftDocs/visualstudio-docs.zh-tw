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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e5284ae41f961d8e027590b4296037236e7108f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699441"
---
# <a name="intrinsic-functions"></a>內建函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SAL 中的運算式可以是 C/C++ 運算式 (假設該運算式沒有副作用的話)，例如 ++、-- 和函式呼叫在這個內容中全都有副作用。  不過，SAL 提供一些類似的函式物件和一些可以用於 SAL 運算式的保留的符號。 這些指*內建函式*。  
  
## <a name="general-purpose"></a>一般用途  
 下列內建函式註釋提供 SAL 的一般公用程式。  
  
|註釋|描述|  
|----------------|-----------------|  
|`_Curr_`|目前標註之物件的同義字。  正在使用 `_At_` 註釋時，`_Curr_` 和 `_At_` 的第一個參數相同。  否則，它會是與註釋在語彙上相關聯的參數或整個函式/傳回值。|  
|`_Inexpressible_(expr)`|表示緩衝區的大小太複雜而無法使用註釋運算式表示的情況，例如，透過掃描輸入資料集，然後計算所選取成員的方式計算。|  
|`_Nullterm_length_(param)`|`param` 已達緩衝區，但不包括 null 結束字元的項目數。 您可能會套用至任何非彙總、 非 void 類型的緩衝區。|  
|`_Old_(expr)`|在前置條件下進行評估時，`_Old_` 會傳回輸入值 `expr`。  在後置條件下進行評估時，它會傳回值 `expr`，因為它已在前置條件下進行評估。|  
|`_Param_(n)`|`n`個參數的函式，從 1 到計算`n`，和`n`是常值的整數常數。 如果參數的名稱，就有一個此註解等同於依名稱存取的參數。 **注意︰** `n`可能會參考省略符號，定義，或可用函式原型中不使用名稱的位置參數。|  
|`return`|C /C++保留的關鍵字`return`可以用於 SAL 運算式來表示函式的傳回值。  值只能在後置狀態下使用，因此在前置狀態下使用就是語法錯誤。|  
  
## <a name="string-specific"></a>特定的字串  
 下列內建函式註釋可讓您操作字串。 這四種函式的目的都相同：傳回 null 結束字元之前所找到類型的項目數。 差異在於項目中參考的資料類型。 請注意，如果您要指定不是以字元組成之以 null 終止的緩衝區長度，請使用前一節中的 `_Nullterm_length_(param)` 註釋。  
  
|註釋|描述|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` 是中的字串，最多，但不是包括 null 結束字元的項目數。 此註解會保留給字串的字元類型。|  
|`strlen(param)`|`param` 是中的字串，最多，但不是包括 null 結束字元的項目數。 此註解會保留供使用的字元陣列，而且類似 C 執行階段函式[strlen （)](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)。|  
|`wcslen(param)`|`param` 是字串直到 （但不是包括） 中的項目數 null 結束字元。 此註解會保留供寬字元陣列，而且類似 C 執行階段函式[wcslen （)](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 註釋減少 C /C++程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
