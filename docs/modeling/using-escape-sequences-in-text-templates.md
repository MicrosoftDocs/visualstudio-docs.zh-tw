---
title: 使用文字範本中的逸出序列
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de30faec90fd59531187d09f7eef76c3db7b043
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910437"
---
# <a name="using-escape-sequences-in-text-templates"></a>使用文字範本中的逸出序列
您可以使用逸出序列，文字範本產生文字範本標記中，及 （在 C# 僅限程式碼） 來逸出控制字元和引號。

 若要列印至輸出檔的標準程式碼區塊的開盤和收盤標記，逸出標記，如下所示：

```
\<# ... \#>
```

 您可以執行相同的其他文字範本指示詞和程式碼區塊標籤。

 如果文字區塊包含用來逸出文字範本標記的字串，您可以使用下列的逸出序列：

-   如果文字範本標記會加上偶數數目的逸出 (\\) 字元範本剖析器會包含逸出字元的一半，且包含做為文字範本標記的順序。 例如，如果在文字範本中有四個逸出字元，會有兩個 「\\"產生的檔案中的字元。

-   如果文字範本標記會加上奇數數目的逸出 (\\) 個字元，範本剖析器將包含的下半部 」\\"字元再加上標記本身 (\<# >)。 標記是不被視為文字範本標記。

-   如果逸出 (\\) 字元出現以外，它會逸出控制字元或引號 （在僅限 C#) 的任何序列中的其他任何地方時，會直接輸出的字元。

## <a name="see-also"></a>另請參閱

- [如何：藉由使用逸出序列從範本產生範本](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)