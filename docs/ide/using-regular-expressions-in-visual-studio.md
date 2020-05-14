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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568616"
---
# <a name="use-regular-expressions-in-visual-studio"></a>在 Visual Studio 中使用規則運算式

Visual Studio 會使用 [.NET 規則運算式](/dotnet/standard/base-types/regular-expressions)來尋找和取代文字。

## <a name="regular-expression-examples"></a>規則運算式範例

下表包含一些規則運算式字元、運算子、建構及模式的範例。 如需更完整的參考，請參閱[規則運算式語言](/dotnet/standard/base-types/regular-expression-language-quick-reference)。

|目的|運算是|範例|
|-------------|----------------|-------------|
|比對任何單一字元 (分行符號除外)。 如需詳細資訊，請參閱[任何字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-)。|.|`a.o`匹配"周圍"和"abo"中的"aabo"在"關於"，但不是"acro"在"跨"|
|比對先前運算式中零個或多個項目 (比對的字元越多越好)。 如需詳細資訊，請參閱[比對零或多次](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)。|*|`a*r` 會比對 "rack" 中的 "r"、"ark" 中的 "ar"，以及 "aardvark" 中的 "aar"|
|匹配任何字元零次或更多次。|.*|`c.*e` 會比對 "racket" 中的 "cke"、"comment" 中的 "comme"，以及 "code" 中的 "code"|
|比對先前運算式中一個或多個項目 (比對的字元越多越好)。 如需詳細資訊，請參閱[比對一或多次](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)。|+|`e+d`匹配"饋線"中的"eed"和"ed"在"已褪色"|
|一或多次比對任何字元。|.+|`e.+e`匹配"饋送器"中的"eede"，但在"進料"中找不到匹配項|
|比對先前運算式中零個或多個項目 (比對的字元越少越好)。 如需詳細資訊，請參閱[比對零或多次 (Lazy (忽略優先) 比對)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-)。|*?|`\w*?d`匹配"fad"和"ed"在"褪色"，但不是整個單詞"褪色"由於懶惰匹配|
|比對先前運算式中一個或多個項目 (比對的字元越少越好)。 如需詳細資訊，請參閱[比對一或多次 (Lazy (忽略優先) 比對)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-)。|+?|`e\w+?`匹配"ee"在"睡眠"和"ed"在"褪色"，但在"褪色"中找不到匹配項|
|將比對字串錨定至[行首或字串開頭](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car`匹配單詞"汽車"，只有當它出現在一行的開頭|
|將比對字串錨定至[行尾](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$`匹配"汽車"，只有當它出現在行的末尾|
|將比對字串錨定至檔案結尾|$|`car$`僅當"汽車"出現在檔末尾時，才匹配"汽車"|
|比對集合中的任何單一字元|[abc]|`b[abc]`匹配"ba"，"bb"和"bc"|
|比對字元範圍之間的任何字元|[a-f]|`be[n-t]`匹配"之間的""下注"，"下"中的"ben"和"bes"在"旁邊"，但在"下面"中找不到匹配項|
|擷取和隱含編號包含在括號內的運算式|()|`([a-z])X\1` 會比對 "aXa" 和 "bXb"，但不比對 "aXb"。 "\1" 表示第一個運算式群組 "[a-z]"。 如需詳細資訊，請參閱[擷取群組和取代模式](#capture-groups-and-replacement-patterns)。 |
|使比對失效|(?!abc)|`real(?!ity)` 會比對 "realty" 和 "really" 中的 "real"，但不比對 "reality" 中的 "real"。 它也會在 "realityreal" 中找到第二個 "real" (但不是第一個 "real")。|
|比對任何不在一組特定字元中的字元。 如需詳細資訊，請參閱[負字元群組](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-)。|[^abc]|`be[^n-t]`匹配"之前"中的"bef"，"後面"中的"beh"和"下面"中的"bef"，但在"下面"中找不到匹配項|
|比對符號之前或之後的運算式|&#124;|`(sponge|mud) bath`匹配"海綿浴"和"泥浴"|
|[逸出反斜線之後的字元](/dotnet/standard/base-types/character-escapes-in-regular-expressions)| \\ |`\^`匹配字元 ||
|指定前置字元或群組的出現次數。 如需詳細資訊，請參閱[比對 n 次](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n)。|{n}，其中 'n' 是發生次數|`x(ab){2}x`匹配"xababx"<br/>`x(ab){2,3}x`匹配"xababx"和"沙巴巴克斯"，但不是"沙巴巴布斯"|
|[比對 Unicode 類別中的文字](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p)。 如需 Unicode 字元類別的詳細資訊，請參閱 [Unicode Standard 5.2 字元屬性](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)。|\p{X}，其中 "X" 是 Unicode 數字。|`\p{Lu}`匹配"湯瑪斯·多伊"中的"T"和"D"|
|[比對字邊界](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (在字元類別之外 `\b` 會指定字邊界，在字元類別 `\b` 內則會指定退格鍵。)|`\bin`匹配"in"在"內部"，但在"pinto"中找不到匹配項|
|比對分行符號 (即歸位字元後面接著新行)|\r?\n|`End\r?\nBegin`僅當"結束"是行中的最後一個字串，"開始"是下一行中的第一個字串時，才匹配"結束"和"開始"|
|比對任何[文字字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd`匹配"添加"和"a1d"，但不是"a d"|
|比對任何[空白字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface`匹配短語"公共介面"|
|比對任何[十進位數字字元](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d`匹配"wd40"中的"4"和"0"|

將某些運算子和構造合併以匹配十六進位數的示例正則運算式是`\b0[xX]([0-9a-fA-F]+\)\b`。 此運算式與"0xc67f"匹配，但不匹配"0xc67g"。

> [!TIP]
> 在 Windows 作業系統中，大部分的程式行都是以 "\r\n" 結尾 (歸位字元後面接著新行)。 這些字元不可見，但存在於編輯器中並傳遞給 .NET 正則運算式服務。

## <a name="capture-groups-and-replacement-patterns"></a>擷取群組和取代模式

擷取群組會描寫規則運算式的子運算式，以及擷取輸入字串的子字串。 您可以使用規則運算式本身內部 (例如，尋找重複的字詞)，或取代模式中擷取的群組。 如需詳細資訊，請參閱[規則運算式中的群組建構](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)。

若要建立編號的擷取群組，請用規則運算式模式中的括弧括住子運算式。 擷取會依據規則運算式中的左括號的位置，由左至右自動編號。 存取擷取的群組：

- **在正則運算式中**：`\number`使用 。 例如，規則運算式 `(\w+)\s\1` 中的 `\1` 參考第一個擷取群組 `(\w+)`。

- **在替換模式**：使用`$number`。 例如，已分組的規則運算式 `(\d)([a-z])` 會定義兩個群組：第一個群組包含單一的十進位數字，第二個群組包含介於 **a** 和 **z** 之間的單一字元。 運算式在下列字串中找到四個相符項目：**1a 2b 3c 4d**。 取代字串 `z$1` 只參考第一個群組 (`$1`)，並將字串轉換成 **z1 z2 z3 z4**。

下圖顯示規則運算式 `(\w+)\s\1` 和取代字串 `$1`。 規則運算式和取代模式會參考自動編號為 1 的第一個擷取群組。 當您在 Visual Studio 的 [快速取代]**** 對話方塊中選擇 [全部取代]**** 時，會將重複的字組從文字中移除。

![Visual Studio 中顯示編號擷取群組的快速取代](media/numbered-capture-group.png)

> [!TIP]
> 請確定已選取 [快速取代]**** 對話方塊中的 [使用規則運算式]**** 按鈕。

### <a name="named-capture-groups"></a>具名的擷取群組

您可以改為為擷取群組命名，不使用自動編號。 具的擷取群組的語法為 `(?<name>subexpression)`。

具名擷取群組 (例如編號的擷取群組)，可在規則運算式本身或在取代模式中使用。 存取具名擷取群組：

- **在正則運算式中**：`\k<name>`使用 。 例如，規則運算式 `(?<repeated>\w+)\s\k<repeated>` 中的 `\k<repeated>` 參考名稱為 `repeated` 且子運算式為 `\w+` 的擷取群組。

- **在替換模式**：使用`${name}`。 例如： `${repeated}` 。

舉例來說，下圖顯示規則運算式 `(?<repeated>\w+)\s\k<repeated>` 和取代字串 `${repeated}`。 規則運算式和取代模式會參考名為 `repeated` 的擷取群組。 當您在 Visual Studio 的 [快速取代]**** 對話方塊中選擇 [全部取代]**** 時，會將重複的字組從文字中移除。

![Visual Studio 中顯示具名擷取群組的快速取代](media/named-capture-group.png)

> [!TIP]
> 請確定已選取 [快速取代]**** 對話方塊中的 [使用規則運算式]**** 按鈕。

如需具名擷取群組的詳細資訊，請參閱[具名的相符子運算式](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions)。 如需取代模式中所用規則運算式的詳細資訊，請參閱[規則運算式中的替代項目](/dotnet/standard/base-types/substitutions-in-regular-expressions)。

## <a name="see-also"></a>另請參閱

- [規則運算式語言](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [查找和替換文本](../ide/finding-and-replacing-text.md)
