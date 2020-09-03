---
title: 指定套用注釋的時機和位置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1eb32aa7d87da75ebf37b27aa1d425adb85f8c9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278462"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>指定套用註釋的時機和位置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當批註是條件式時，可能需要其他注釋來指定分析器的附注。  例如，如果函式的變數可以是同步或非同步，函式的行為會如下所示：在同步的情況下，它一律會成功，但是在非同步情況下，它會在無法立即成功時報告錯誤。 以同步方式呼叫函式時，檢查結果值不會對程式碼分析器提供任何值，因為它不會傳回。  不過，當以非同步方式呼叫函式並不檢查函數結果時，可能會發生嚴重的錯誤。 此範例說明您可以使用批註的情況 `_When_` （如本文稍後所述），以啟用檢查。  
  
## <a name="structural-annotations"></a>結構化批註  
 若要控制批註套用的時機和位置，請使用下列結構化批註。  
  
|Annotation|說明|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` 這是會產生左值的運算式。 中的注釋 `anno-list` 會套用至由命名的物件 `expr` 。 針對中的每個批註 `anno-list` ， `expr` 如果批註是在前置條件中轉譯，則會在前置條件中解讀，如果批註是在後置條件中解釋，則為。|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` 這是會產生左值的運算式。 中的注釋 `anno-list` 會套用至由命名的物件 `expr` 。 針對中的每個批註 `anno-list` ， `expr` 如果批註是在前置條件中解讀，則會在前置條件中解讀，如果批註是在後置條件中解讀則為。<br /><br /> `iter` 這是範圍設定為注釋 (包含) 之變數的名稱 `anno-list` 。 `iter` 具有隱含類型 `long` 。 任何封入範圍中同名的變數都不會進行評估。<br /><br /> `elem-count` 這是評估為整數的運算式。|  
|`_Group_(anno-list)`|中的批註 `anno-list` 全都被視為具有適用于每個批註之群組注釋的任何限定詞。|  
|`_When_(expr, anno-list)`|`expr` 這是可以轉換為的運算式 `bool` 。 當) 為非零 (時 `true` ，中指定的注釋 `anno-list` 會被視為適用。<br /><br /> 根據預設， `anno-list` `expr` 如果批註是前置條件，則會將中的每個注釋轉譯為使用輸入值，並在批註為後置條件時使用輸出值。 若要覆寫預設值，您可以在 `_Old_` 評估後置條件時使用內建，以指出應該使用輸入值。 **注意：**  使用時，可能會因為使用可變動的 `_When_` 值（例如，）而啟用不同的注釋， `*pLength` 因為先決條件的評估結果 `expr` 可能與後續條件中的評估結果不同。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 注釋減少 C/c + + 程式碼瑕疵](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [瞭解 SAL](../code-quality/understanding-sal.md)   
 [標注函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [標注函式行為](../code-quality/annotating-function-behavior.md)   
 [標注結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [標注鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
