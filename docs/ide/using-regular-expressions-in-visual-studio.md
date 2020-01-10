---
title: 使用規則運算式
ms.date: 09/13/2019
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568616"
---
# <a name="use-regular-expressions-in-visual-studio"></a>在 Visual Studio 中使用規則運算式

Visual Studio 會使用 [.NET 規則運算式](/dotnet/standard/base-types/regular-expressions)來尋找和取代文字。

## <a name="regular-expression-examples"></a>規則運算式範例

下表包含一些規則運算式字元、運算子、建構及模式的範例。 如需更完整的參考，請參閱[規則運算式語言](/dotnet/standard/base-types/regular-expression-language-quick-reference)。

|用途|運算式|範例|
|-------------|----------------|-------------|
|比對任何單一字元 (分行符號除外)。 如需詳細資訊，請參閱[任何字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-)。|。|`a.o` 比對「關於」中的「aro」和「關於」中的「abo」，但不符合「跨」中的「acro」|
|比對先前運算式中零個或多個項目 (比對的字元越多越好)。 如需詳細資訊，請參閱[比對零或多次](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)。|*|`a*r` 會比對 "rack" 中的 "r"、"ark" 中的 "ar"，以及 "aardvark" 中的 "aar"|
|比對任何字元零或多次。|.*|`c.*e` 會比對 "racket" 中的 "cke"、"comment" 中的 "comme"，以及 "code" 中的 "code"|
|比對先前運算式中一個或多個項目 (比對的字元越多越好)。 如需詳細資訊，請參閱[比對一或多次](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)。|+|`e+d` 符合「送紙器」中的 "eed" 和「淡出」中的 "ed"|
|一或多次比對任何字元。|.+|`e.+e` 符合「送紙器」中的「對 feeder」，但在「摘要」中找不到相符專案|
|比對先前運算式中零個或多個項目 (比對的字元越少越好)。 如需詳細資訊，請參閱[比對零或多次 (Lazy (忽略優先) 比對)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-)。|*?|`\w*?d` 符合「褪色」中的 "fad" 和 "ed"，而不是整個單字「褪色」，因為延遲相符|
|比對先前運算式中一個或多個項目 (比對的字元越少越好)。 如需詳細資訊，請參閱[比對一或多次 (Lazy (忽略優先) 比對)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-)。|+?|`e\w+?` 比對「休眠」和「ed」中「淡出」的「ee」，但在「淡化」中找不到相符專案|
|將比對字串錨定至[行首或字串開頭](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|只有當它出現在行首時，`^car` 才會符合 "car" 這個字|
|將比對字串錨定至[行尾](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|只有當它出現在行尾時，`car\r?$` 才會符合 "car"|
|將比對字串錨定至檔案結尾|$|只有當它出現在檔案結尾時，`car$` 才會符合 "car"|
|比對集合中的任何單一字元|[abc]|`b[abc]` 符合 "ba"、"bb" 和 "bc"|
|比對字元範圍之間的任何字元|[a-f]|`be[n-t]` 符合 "a" 中的 "a"、"ben" （在「底下」）和「旁」中的「be」，但在「以下」中找不到相符專案|
|擷取和隱含編號包含在括號內的運算式|()|`([a-z])X\1` 會比對 "aXa" 和 "bXb"，但不比對 "aXb"。 "\1" 表示第一個運算式群組 "[a-z]"。 如需詳細資訊，請參閱[擷取群組和取代模式](#capture-groups-and-replacement-patterns)。 |
|使比對失效|(?!abc)|`real(?!ity)` 會比對 "realty" 和 "really" 中的 "real"，但不比對 "reality" 中的 "real"。 它也會在 "realityreal" 中找到第二個 "real" (但不是第一個 "real")。|
|比對任何不在一組特定字元中的字元。 如需詳細資訊，請參閱[負字元群組](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-)。|[^abc]|`be[^n-t]` 符合 "before"、"beh" 中 "bef" 和 "bel" 中 "" 的 ""，但在 "底下" 中找不到相符專案|
|比對符號之前或之後的運算式|&#124;|`(sponge|mud) bath` 符合「海綿浴缸」和「mud 浴缸」|
|[逸出反斜線之後的字元](/dotnet/standard/base-types/character-escapes-in-regular-expressions)| \\ |`\^` 符合字元 ^|
|指定前置字元或群組的出現次數。 如需詳細資訊，請參閱[比對 n 次](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n)。|{n}，其中 'n' 是發生次數|`x(ab){2}x` 符合 "對 xababx"<br/>`x(ab){2,3}x` 比對 "對 xababx" 和 "xabababx"，但不符合 "比對 xababababx"|
|[比對 Unicode 類別中的文字](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p)。 如需 Unicode 字元類別的詳細資訊，請參閱 [Unicode Standard 5.2 字元屬性](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)。|\p{X}，其中 "X" 是 Unicode 數字。|`\p{Lu}` 符合 "Thomas Doe" 中的 "T" 和 "D"|
|[比對字邊界](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (在字元類別之外 `\b` 會指定字邊界，在字元類別 `\b` 內則會指定退格鍵。)|`\bin` 符合「內部」中的 "in"，但在 "pinto" 中找不到相符專案|
|比對分行符號 (即歸位字元後面接著新行)|\r?\n|只有在 "End" 是一行的最後一個字串，且 "Begin" 是下一行的第一個字串時，`End\r?\nBegin` 才會符合 "End" 和 "Begin"|
|比對任何[文字字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` 符合 "add" 和 "a1d"，而不是 "a d"|
|比對任何[空白字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` 符合「公用介面」一詞|
|比對任何[十進位數字字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` 符合 "wd40" 中的 "4" 和 "0"|

`\b0[xX]([0-9a-fA-F]+\)\b`，結合一些運算子和結構以符合十六進位數位的範例正則運算式。 這個運算式會比對 "對 0xc67f"，但不符合 "0xc67g"。

> [!TIP]
> 在 Windows 作業系統中，大部分的程式行都是以 "\r\n" 結尾 (歸位字元後面接著新行)。 這些字元並不可見，但會出現在編輯器中，並傳遞至 .NET 正則運算式服務。

## <a name="capture-groups-and-replacement-patterns"></a>擷取群組和取代模式

擷取群組會描寫規則運算式的子運算式，以及擷取輸入字串的子字串。 您可以使用規則運算式本身內部 (例如，尋找重複的字詞)，或取代模式中擷取的群組。 如需詳細資訊，請參閱[規則運算式中的群組建構](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)。

若要建立編號的擷取群組，請用規則運算式模式中的括弧括住子運算式。 擷取會依據規則運算式中的左括號的位置，由左至右自動編號。 存取擷取的群組：

- 在**正則運算式內**：使用 `\number`。 例如，規則運算式 `(\w+)\s\1` 中的 `\1` 參考第一個擷取群組 `(\w+)`。

- **在取代模式中**：使用 `$number`。 例如，已分組的規則運算式 `(\d)([a-z])` 會定義兩個群組：第一個群組包含單一的十進位數字，第二個群組包含介於 **a** 和 **z** 之間的單一字元。 運算式在下列字串中找到四個相符項目：**1a 2b 3c 4d**。 取代字串 `z$1` 只參考第一個群組 (`$1`)，並將字串轉換成 **z1 z2 z3 z4**。

下圖顯示規則運算式 `(\w+)\s\1` 和取代字串 `$1`。 規則運算式和取代模式會參考自動編號為 1 的第一個擷取群組。 當您在 Visual Studio 的 [快速取代] 對話方塊中選擇 [全部取代] 時，會將重複的字組從文字中移除。

![Visual Studio 中顯示編號擷取群組的快速取代](media/numbered-capture-group.png)

> [!TIP]
> 請確定已選取 [快速取代] 對話方塊中的 [使用規則運算式] 按鈕。

### <a name="named-capture-groups"></a>具名的擷取群組

您可以改為為擷取群組命名，不使用自動編號。 具的擷取群組的語法為 `(?<name>subexpression)`。

具名擷取群組 (例如編號的擷取群組)，可在規則運算式本身或在取代模式中使用。 存取具名擷取群組：

- 在**正則運算式內**：使用 `\k<name>`。 例如，規則運算式 `(?<repeated>\w+)\s\k<repeated>` 中的 `\k<repeated>` 參考名稱為 `repeated` 且子運算式為 `\w+` 的擷取群組。

- **在取代模式中**：使用 `${name}`。 例如，`${repeated}`。

舉例來說，下圖顯示規則運算式 `(?<repeated>\w+)\s\k<repeated>` 和取代字串 `${repeated}`。 規則運算式和取代模式會參考名為 `repeated` 的擷取群組。 當您在 Visual Studio 的 [快速取代] 對話方塊中選擇 [全部取代] 時，會將重複的字組從文字中移除。

![Visual Studio 中顯示具名擷取群組的快速取代](media/named-capture-group.png)

> [!TIP]
> 請確定已選取 [快速取代] 對話方塊中的 [使用規則運算式] 按鈕。

如需具名擷取群組的詳細資訊，請參閱[具名的相符子運算式](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions)。 如需取代模式中所用規則運算式的詳細資訊，請參閱[規則運算式中的替代項目](/dotnet/standard/base-types/substitutions-in-regular-expressions)。

## <a name="see-also"></a>請參閱

- [規則運算式語言](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [尋找及取代文字](../ide/finding-and-replacing-text.md)
