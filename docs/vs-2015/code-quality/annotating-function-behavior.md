---
title: 註釋函式行為 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 39edea3bfb299a49fde9cad14321caa6b4bf674a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157093"
---
# <a name="annotating-function-behavior"></a>註釋函式行為
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

除了標註[函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)，您可以標註整體函式的屬性。  
  
## <a name="function-annotations"></a>函式註釋  
 下列註釋適用於整個函式，並描述它的行為或它預期成立的項目。  
  
|註釋|描述|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|這個述詞不適合單獨使用，而是要搭配 `_When_` 註釋使用。 如需詳細資訊，請參閱 <<c0> [ 指定時，並在註釋套用](../code-quality/specifying-when-and-where-an-annotation-applies.md)。<br /><br /> `name`參數是任意字串，也會出現在`_Function_class_`的某些函式宣告中的註解。  `_Called_from_function_class_` 傳回非零值，如果目前正在分析函式使用標註`_Function_class_`具有相同值的`name`，否則會傳回零。|  
|`_Check_return_`|標註傳回值，並指出呼叫端應檢查該值。 如果函式是在 void 內容中呼叫，則檢查程式會報告錯誤。|  
|`_Function_class_(name)`|`name` 參數是使用者指定的任意字串。  它會存在彼此不同的命名空間中。 函式、函式指標或最常見的函式指標類型都可以指定為屬於一個或多個函式類別。|  
|`_Raises_SEH_exception_`|標註一定會引發結構化例外狀況處理常式 (SEH) 例外狀況的函式 (受 `_When_` 和 `_On_failure_` 條件所限制)。 如需詳細資訊，請參閱 <<c0> [ 指定時，並在註釋套用](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|  
|`_Maybe_raises_SEH_exception_`|標註可以選擇性引發 SEH 例外狀況的函式 (受 `_When_` 和 `_On_failure_` 條件所限制)。|  
|`_Must_inspect_result_`|標註任何輸出值，包括傳回值、 參數和全域變數。  如果在標註的物件中未接著檢查值，分析器就會報告錯誤。 「檢查」包括值是否用於條件運算式、指派給輸出參數或全域，或是做為參數傳遞。  傳回值，如`_Must_inspect_result_`意味著`_Check_return_`。|  
|`_Use_decl_annotations_`|可能會代替函式定義 （也稱為函式主體） 上的標頭中的註解清單。  當`_Use_decl_annotations_`會出現在相同的函式的範圍內標頭的註解使用如同它們也會出現在已定義`_Use_decl_annotations_`註釋。|  
  
## <a name="successfailure-annotations"></a>成功/失敗的註解  
 函式可能會失敗，當它失敗時，其結果可能不完整或與函式成功時的結果不同。  下列清單中的註釋提供了表示失敗行為的方式。  若要使用這些註釋，您必須啟用它們來判斷是否成功，因此必須有 `_Success_` 註釋。  請注意，`NTSTATUS` 和 `HRESULT` 已有內建的 `_Success_` 註釋。不過，如果您在 `_Success_` 或 `NTSTATUS` 上指定自己的 `HRESULT` 註釋，它就會覆寫內建註釋。  
  
|註釋|說明|  
|----------------|-----------------|  
|`_Always_(anno_list)`|相當於 `anno_list _On_failure_(anno_list)`，也就是說，無論函式是否成功，都會套用 `anno_list` 中的註釋。|  
|`_On_failure_(anno_list)`|只有在同時使用 `_Success_` 標註函式時才使用，無論是明確使用，或是在 typedef 上透過 `_Return_type_success_` 隱含使用。 當 `_On_failure_` 註釋出現在函式參數或傳回值上時，在 `anno_list` (anno) 中每個註釋的行為就如同撰寫成 `_When_(!expr, anno)` 的程式碼，其中 `expr` 是所需 `_Success_` 註釋的參數。 這表示，對所有後置條件的 `_Success_` 的隱含用法不適用於 `_On_failure_`。|  
|`_Return_type_success_(expr)`|可套用至 typedef。 指出傳回該類型且未明確擁有 `_Success_` 的所有函式，都會標註為如同擁有 `_Success_(expr)`。 `_Return_type_success_` 無法在函式或函式指標 typedef 上使用。|  
|`_Success_(expr)`|`expr` 是產生右值的運算式。 當 `_Success_` 註釋出現在函式宣告或定義上時，函式上和後置條件中每個註釋 (`anno`) 的行為就如同撰寫為 `_When_(expr, anno)` 程式碼一樣。 `_Success_` 註釋只能在函式上使用，而不能在其參數或傳回型別上使用。 函式上最多只能有一個 `_Success_` 註釋，而且不能在任何 `_When_`、`_At_` 或 `_Group_` 中。 如需詳細資訊，請參閱 <<c0> [ 指定時，並在註釋套用](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 註釋減少 C /C++程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
