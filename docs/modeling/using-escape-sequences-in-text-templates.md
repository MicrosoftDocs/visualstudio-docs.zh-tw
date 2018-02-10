---
title: "在文字範本中使用逸出序列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f6ab5346ed82aadea339bc8ee45ac4a3bfb72c65
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>使用文字範本中的逸出序列
您可以使用逸出序列，在文字範本產生文字範本的標籤和 （在 C# 僅限程式碼） 來逸出控制字元和引號。  
  
 若要列印至輸出檔的標準程式碼區塊的開盤和收盤標記，逸出標記，如下所示：  
  
```  
\<# ... \#>  
```  
  
 您可以執行相同的其他文字範本指示詞和程式碼區塊標記。  
  
 如果文字區塊包含用來逸出的文字範本標記的字串，您可以使用下列的逸出序列：  
  
-   如果文字範本標記加上偶數數目的逸出 (\\) 字元範本剖析器會包含逸出字元的下半部，並包含為文字範本標記順序。 例如，如果在文字範本中有四個逸出字元，會有兩個 「\\」 所產生的檔案中的字元。  
  
-   如果文字範本標記已加上逸出為奇數 (\\) 字元，範本的剖析器將包含的下半部"\\"字元再加上標記本身 (\<# >)。 標記是不被視為文字範本標記。  
  
-   如果逸出 (\\) 字元會顯示任何以外，它控制字元或引號 （在僅限 C#) 來逸出序列中的其他地方，直接將輸出的字元。  
  
## <a name="see-also"></a>請參閱  
 [如何：使用逸出序列從範本產生範本](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)