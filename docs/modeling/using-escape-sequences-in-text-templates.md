---
title: "在文字範本中使用逸出序列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fdf062c9b33dd4a160f54bba83991a3cdda7f0d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
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
  
## <a name="see-also"></a>另請參閱  
 [如何：使用逸出序列從範本產生範本](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)