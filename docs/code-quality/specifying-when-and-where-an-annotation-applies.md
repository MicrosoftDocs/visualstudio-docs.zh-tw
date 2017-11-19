---
title: "指定套用註釋的時機和位置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5bfff9eb7e2040d5a4b75fa82c2a504f2aaeceda
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>指定套用註釋的時機和位置
條件式註解時，它可能需要其他註解來指定分析器。  例如，如果函式可以是同步或非同步的變數、 函式的行為，如下所示： 在同步的情況下它一定最終會成功，但是非同步案例中才會報告錯誤無法立即成功時，則。 以同步方式呼叫此函式時，檢查結果值提供以程式碼分析工具的任何值，因為它將不會有傳回。  不過，當函式會以非同步方式呼叫，就不會檢查函式的結果，無法發生嚴重的錯誤。 此範例說明您可以使用的情況下`_When_`註釋，本文稍後所述，啟用檢查。  
  
## <a name="structural-annotations"></a>結構化的註解  
 若要控制註釋套用的時機和位置，請使用下列結構的註解。  
  
|註釋|說明|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr`這是會產生左值的運算式。 中的註解`anno-list`套用至物件命名`expr`。 每個註釋中`anno-list`，`expr`解譯都是前置條件如果註解的解譯都是前置條件，而且在後置條件如果註解的解譯都是後置條件。|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`這是會產生左值的運算式。 中的註解`anno-list`套用至物件命名`expr`。 每個註釋中`anno-list`，`expr`解譯都是前置條件如果註解的解譯都是前置條件，而且在後置條件如果註解的解譯都是後置條件。<br /><br /> `iter`是以註解為範圍之變數的名稱 (在內`anno-list`)。 `iter`具有隱含型別`long`。 在任何封閉範圍中同名的變數會從評估中隱藏。<br /><br /> `elem-count`這是判斷值為整數的運算式。|  
|`_Group_(anno-list)`|中的註解`anno-list`全部都視為具有群組註釋套用至每個註釋適用於任何限定詞。|  
|`_When_(expr, anno-list)`|`expr`運算式可以轉換成`bool`。 當它為非零 (`true`) 中, 指定的註解`anno-list`被視為適用。<br /><br /> 根據預設，每個註釋中`anno-list`，`expr`解譯為使用輸入的值，如果註釋會在前置條件，而且如果使用的輸出值為註解是後置條件。 若要覆寫預設值，您可以使用`_Old_`評估以指出應該使用輸入的值的後置條件時，內建函式。 **注意：**可能由於使用啟用不同的註解`_When_`如果可變動的值 — 比方說， `*pLength`— 因為涉及評估的結果的`expr`在前置條件下，可能會有所不同其評估會導致後置條件。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 註釋減少 C/c + + 程式碼缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)