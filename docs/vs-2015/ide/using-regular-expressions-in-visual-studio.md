---
title: 在 Visual Studio 中使用規則運算式 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
- Visual Studio, regular expressions
ms.assetid: 718a617d-0e05-47e1-a218-9746971527f4
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4edf0add3e29dd7fe4156a220fe0edc60e47f117
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285463"
---
# <a name="use-regular-expressions-in-visual-studio"></a>在 Visual Studio 中使用規則運算式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio 會使用.NET Framework 規則運算式來尋找和取代文字。 如需 .NET 規則運算式的詳細資訊，請參閱 [.NET Framework 規則運算式](http://msdn.microsoft.com/library/521b3f6d-f869-42e1-93e5-158c54a6895d)。

在 Visual Studio 2012 之前，Visual Studio 在 [尋找和取代] 視窗中使用自訂的規則運算式語法。 如需如何將一些常用的自訂規則運算式符號轉換成該 .NET 版本之說明，請參閱 [Visual Studio Regular Expression Conversions](https://msdn.microsoft.com/library/2k3te2cs\(v=vs.110\).aspx) (Visual Studio 規則運算式轉換)。

> [!TIP]
> 在 Windows 作業系統中，大部分的程式行都是以 "\r\n" 結尾 (歸位字元後面接著新行)。 這些字元並不可見，但是會顯示在編輯器中，並傳遞至 .NET 規則運算式服務。

> [!TIP]
> 如需取代模式中所用規則運算式的資訊，請參閱[替代](http://msdn.microsoft.com/library/d1f52431-1c7d-4dc6-8792-6b988256892e)。 若要使用已編號的擷取群組，指定編號的群組之語法為 `$1`，以及使用 `(x)` 指定考慮中的此群組。 例如，群組規則運算式 `(\d)([a-z])` 在下列字串中找到四個相符項目：**1a 2b 3c 4d**。 取代字串 `z$1` 會將該字串轉換為 **z1 z2 z3 z4**。

## <a name="regular-expression-examples"></a>規則運算式範例

以下是一些範例：

|用途|運算式|範例|
|-------------|----------------|-------------|
|比對任何單一字元 (分行符號除外)|。|`a.o` 會比對 "around" 中的 "aro" 和 "about" 中的 "abo"，但不比對 "across" 中的 "acro"。|
|比對先前運算式中零個或多個項目 (比對的字元越多越好)|*|`a*r` 會比對 "rack" 中的 "r"、"ark" 中的 "ar"，以及 "aardvark" 中的 "aar"|
|比對任何字元零或多次 (萬用字元 *)|.*|c.*e 會比對 “racket” 中的“cke”、“comment” 中的 “comme”，以及 “code” 中的 “code”|
|比對先前運算式中一個或多個項目 (比對的字元越多越好)|+|`e.+e` 會比對 "feeder" 中的 "eede"，但不比對 "ee"。|
|比對任何字元一或多次 (萬用字元 ?)|.+|e.+e 會比對 "feeder" 中的 "eede"，但不比對 "ee"。|
|比對先前運算式中零個或多個項目 (比對的字元越少越好)|*?|`e.*?e` 會比對 "feeder" 中的 "ee"，但不比對 "eede"。|
|比對先前運算式中一個或多個項目 (比對的字元越少越好)|+?|`e.+?e` 會比對 "enterprise" 中的 "ente" 及 "erprise"，但不比對完整單字 "enterprise"。|
|將比對字串錨定至行首或字串開頭|^|`^car` 只會比對出現在行首的 "car" 這個字。|
|將比對字串錨定至行尾|\r?$|`End\r?$` 只會比對出現在行尾的 "end"。|
|比對集合中的任何單一字元|[abc]|`b[abc]` 會比對 "ba"、"bb" 和 "bc"。|
|比對字元範圍之間的任何字元|[a-f]|`be[n-t]` 會比對 "between" 中的 "bet"、"beneath" 中的 "ben" 和 "beside" 中的 "bes"，但不比對 "below"。|
|擷取和隱含編號包含在括號內的運算式|()|`([a-z])X\1` 會比對 "aXa" 和 "bXb"，但不比對 "aXb"。 ". “\1” 表示第一個運算式群組 “[a-z]”。|
|使比對失效|(?!abc)|`real (?!ity)` 會比對 "realty" 和 "really" 中的 "real"，但不比對 "reality" 中的 "real"。 它也會在 "realityreal" 中找到第二個 "real" (但不是第一個 "real")。|
|比對任何不在特定一組字元中的字元。|[^abc]|`be[^n-t]` 會比對 "before" 中的 "bef"、"behind" 中的 "beh" 和 "below" 中的 "bel"，但不比對 "beneath"。|
|比對符號之前或之後的運算式。|&#124;|`(sponge&#124;mud) bath` 會比對 "sponge bath" 和 "mud bath"。|
|逸出反斜線之後的字元|\|`\^` 比對字元 ^。|
|指定前置字元或群組的出現次數。|{x}，其中 x 是發生次數。|`x(ab){2}x` 會比對 "xababx"，而 `x(ab){2,3}x` 會比對 "xababx" 和 "xabababx"，但不比對 "xababababx"。|
|比對 Unicode 字元類別中的文字，其中 “X” 是 Unicode 數字。 如需 Unicode 字元類別的詳細資訊，請參閱 <br /><br /> [Unicode Standard 5.2 字元屬性](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)。|\p{X}|`\p{Lu}` 會比對 "Thomas Doe" 中的 "T" 和 "D"。|
|比對字邊界|`\b` (在字元類別之外 \b 會指定字邊界，在字元類別內則會指定退格鍵)。|`\bin` 會比對 "inside" 中的 "in"，但不比對 "pinto"。|
|比對分行符號 (即歸位字元後面接著新行)。|\r?\n|`End\r?\nBegin` 只在 "End" 是一行的最後一個字串，且 "Begin" 是下一行的第一個字串時比對 "End" 和 "Begin"。|
|比對任何英數字元|\w|`a\wd` 會比對 "add" 和 "a1d"，但不比對 "a d"。|
|比對任何空白字元。|(?([^\r\n])\s)|`Public\sInterface` 會比對 "Public Interface" 這個片語。|
|比對任何數字字元|\d|`\d` 會比對 "3456" 中的 "3"、"23" 中的 "2" 和 "1" 中的 "1"。|
|比對 Unicode 字元|\uXXXX，其中 XXXX 指定 Unicode 字元值。|`\u0065` 會比對字元 "e"。|
|比對識別項|\b(_\w+&#124;[\w-[0-9\_]]\w*)\b|會比對 "type1"，但不比對 & type1" 或 "#define"。|
|比對引號內的字串|((\\".+?\\")&#124;('.+?'))|比對單引號或雙引號內的任何字串。|
|比對十六進位數字|\b0[xX]([0-9a-fA-F]\)\b|比對 "0xc67f" 但不比對 "0xc67fc67f"。|
|比對整數和小數|\b[0-9]*\\.\*[0-9]+\b|會比對 "1.333"。|