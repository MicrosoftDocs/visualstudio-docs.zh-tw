---
title: 使用文字範本中的逸出序列
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662923"
---
# <a name="use-escape-sequences-in-text-templates"></a>在文字模板中使用 escape 序列

您可以在文字模板中使用 escape 序列，以產生文字模板標記和C# （僅限程式碼）來將控制字元和引號轉義。

若要將標準程式碼區塊的開啟和關閉標記列印到輸出檔案，請如下所示，將標記換成：

```
\<# ... \#>
```

您可以使用其他文字模板指示詞和程式碼區塊標記來執行相同的動作。

如果文字區塊包含用來將文字模板標記轉義的字串，您可以使用下列轉義順序：

- 如果文字模板標記前面加上偶數的 escape （\\）字元，則範本剖析器會包含一半的逸出字元，並包含序列做為文字模板標記。 例如，如果文字模板中有四個換用字元，則產生的檔案中將會有兩個 "\\" 字元。

- 如果文字模板標記前面加上奇數的 escape （\\）字元，則範本剖析器會包含一半的 "\\" 字元加上標記本身（\< # 或 # >）。 標記不會被視為文字模板標記。

- 如果 escape （\\）字元在任何序列中的任何位置出現，而不是將控制字元或引號（ C#僅限）轉義，則會直接輸出該字元。

## <a name="see-also"></a>請參閱

- [如何：使用逸出序列從範本產生範本](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)