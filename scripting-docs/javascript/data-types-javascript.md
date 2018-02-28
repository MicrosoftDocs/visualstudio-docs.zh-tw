---
title: "資料類型 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="data-types-javascript"></a>資料類型 (JavaScript)
在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，有三種主要資料類型、兩個複合資料類型，以及兩個特殊資料類型。  
  
## <a name="primary-data-types"></a>主要資料型別  
 主要 (基本) 資料類型如下：  
  
-   String  
  
-   數字  
  
-   Boolean  
  
## <a name="composite-data-types"></a>複合資料類型  
 複合 (參考) 資料類型如下：  
  
-   物件  
  
-   陣列  
  
## <a name="special-data-types"></a>特殊資料型別  
 特殊資料類型如下：  
  
-   Null  
  
-   未定義  
  
## <a name="string-data-type"></a>String 資料類型  
 字串值是一串零或多個 Unicode 字元 (字母、數字和標點符號)。 您可以使用字串資料類型來呈現 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的文字。 您可以在指令碼中包含字串常值，方法是使用單引號或雙引號予以括住。 以單引號括住的字串中可以包含雙引號，而以雙引號括住的字串中可以包含單引號。 下列是字串範例：  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 請注意，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 沒有類型可呈現單一字元。 若要在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中呈現單一字元，請建立只包含一個字元的字串。 包含零個字元的字串 ("") 是空 (長度為零) 字串。  
  
 您可以在字串中放入 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 提供的逸出序列 (Escape Sequence)，用來建立無法直接輸入的字元。 例如，`\t` 會指定定位字元。 如需詳細資訊，請參閱[特殊字元](../javascript/advanced/special-characters-javascript.md)。  
  
## <a name="number-data-type"></a>數字資料類型  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，無法區別整數與浮點值；[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 數字可以是 (就內部而言，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會將所有數字都呈現為浮點值)。  
  
### <a name="integer-values"></a>整數值  
 整數值可以是正整數、負整數和 0。 它們可以使用基底 10 (十進位)、基底 16 (十六進位) 和基底 8 (八進位) 呈現。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的大部分數字都是以十進位寫入。  
  
 十六進位 ("hex") 整數的表示方式是在前面加上前置 "0x" (零和 x&#124;X)。 它們只能包含數字 0 到 9 以及字母 A 到 F (大寫或小寫)。 字母 A 到 F 是用來代表基底 10 的 10 到 15 (單一數字)。 亦即，0xF 相當於 15，而 0x10 相當於 16。  
  
 八進位整數的表示方式是在前面加上前置 "0" (零)。 它們只能包含數字 0 到 7。 具有前置 "0" 且包含數字 "8" 和 (或) "9" 的數字會解譯為十進位數字。  
  
 十六進位和八進位數字可以是負數，但不能有小數部分，而且無法以科學記號 (指數) 標記法撰寫。  
  
> [!NOTE]
>  從 [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)] 開始，[parseInt 函式](../javascript/reference/parseint-function-javascript.md)不會將前置詞為 "0" 的字串視為八進位。 不過，當您未使用 `parseInt` 函式時，前置詞為 "0" 的字串仍然可以解譯為八進位。  
  
### <a name="floating-point-values"></a>浮點值  
 浮點值可以是含小數部分的整數。 此外，它們還可以使用科學記號標記法表示。 亦即，大寫或小寫 "e" 是用來代表「10 的乘冪」。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 代表使用八位元組 IEEE 754 浮點數標準的數字來進行數值呈現。 這表示您可以撰寫最大數字 1.79769x10<sup>308</sup> 和最小數字 5x10<sup>-324</sup>。 包含小數點且小數點前面具有單一"0"的數字會解譯為十進位浮點數。  
  
 請注意，開頭為 "0x" 或 "00"且包含小數點的數字會產生錯誤。 以下是一些 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 數字範例。  
  
|數字|描述|十進位對等項目|  
|------------|-----------------|------------------------|  
|.0001、0.0001、1e-4、1.0e-4|四個對等的浮點數。|0.0001|  
|3.45e2|浮點數。|345|  
|45|整數。|45|  
|0378|整數。 雖然這看起來像八進位數字 (開頭為零)，但 8 不是有效的八進位數字，因此這個數字視為十進位數字。|378|  
|0377|八進位整數。 請注意，雖然它只是比上述數字小一，但其實際值相當不同。|255|  
|0.0001|浮點數字。 即使這個數字的開頭是零，它也不是八進位數字，因為它有小數點。|0.0001|  
|00.0001|這是錯誤。 兩個前置零會將數字標示為八進位，但八進位不允許有小數部分。|N/A (編譯器錯誤)|  
|0Xff|十六進位整數。|255|  
|0x37CF|十六進位整數。|14287|  
|0x3e7|十六進位整數。 請注意，'e' 不能視為乘冪。|999|  
|0x3.45e2|這是錯誤。 十六進位數字不能有小數部分。|N/A (編譯器錯誤)|  
  
 此外，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 包含具有特殊值的數字。 這些是：  
  
-   NaN (非數字)。 這是在對不適當資料 (例如字串或未定義值) 執行數學運算時使用  
  
-   正無限大。 正數太大而無法在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中呈現時，會使用此項目  
  
-   負無限大。 負數太大而無法在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中呈現時，會使用此項目  
  
-   正和負 0。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 可區分正零和負零。  
  
## <a name="boolean-data-type"></a>Boolean 資料類型  
 雖然字串和數字資料類型幾乎可以有無限多的不同值，但布林值資料類型只能有兩個。 它們是常值 `true` 和 `false`。 布林值是事實值：它指定是否符合條件。  
  
 您在指令碼中進行的比較一律會有布林值結果。 請考慮下列 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼行。  
  
```JavaScript  
y = (x == 2000);  
```  
  
 在這裡，`x` 變數的值會與數字 2000 進行比較。 如果是，則比較結果為指派給變數 `y` 的布林值 **true**。 如果 `x` 不等於 2000，則比較結果是布林值 `false`。  
  
 布林值特別適用於控制結構。 下列程式碼會合併直接建立布林值的比較與使用它的陳述式。 請考慮下列 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼範例。  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 如果布林值為 `true`，則 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的 `if/else` 陳述式會執行一個動作 (`z = z + 1`)；如果布林值為 `false`，則為替代動作 (`x = x + 1`)。  
  
 您可以使用任何運算式作為比較運算式。 評估為 0、Null、未定義或空字串的任何運算式都會解譯為 `false`。 評估為任何其他值的運算式會解譯為 `true`。 例如，您可以使用這類運算式：  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 請注意，上述列不會檢查 `x` 是否等於 `y + z`，因為只會使用單一等號 (指派運算子)。 相反地，上述程式碼會將 `y + z` 的值指派給 `x` 變數，然後檢查整個運算式的結果 (`x` 的值) 是否為零。 若要檢查 `x` 是否等於 `y + z`，您需要使用下列程式碼。  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 如需比較的詳細資訊，請參閱[控制程式流程](../javascript/controlling-program-flow-javascript.md)。  
  
## <a name="the-null-data-type"></a>null 資料型別  
 `null` 資料類型在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中只有一個值：Null。 `null` 關鍵字不能作為函式或變數的名稱。  
  
 包含 `null` 的變數未包含有效的 Number、String、Boolean、Array 或 Object。 您可以將變數指派給 `null` 值，以清除變數的內容 (不需要刪除變數)。  
  
 請注意，在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，`null` 與 0 (在 C 和 C++ 中) 不同。 另請注意，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的 `typeof` 運算子會將 `null` 值報告為類型 `Object`，而非類型 `null`。 這個可能令人混淆的行為是針對回溯相容性。  
  
## <a name="the-undefined-data-type"></a>未定義的資料型別  
 如果您使用不存在的物件屬性或已宣告的變數，但從未指派其值，則會傳回 `undefined` 值。  
  
 您可以比較變數與 `undefined` 來確認變數是否存在，不過您可以比較變數類型與字串 "undefined" 來檢查其類型是 `undefined`。 下列範例示範如何發現已宣告變數 `x`：  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 您也可以比較未定義值與 `null`。 如果屬性 `someObject.prop` 是 `null`，或屬性 `someObject.prop` 不存在，則這項比較為 `true`。  
  
```JavaScript  
someObject.prop == null;  
```  
  
 若要找出物件屬性是否存在，您可以使用 **in** 運算子：  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>另請參閱  
 [物件和陣列](../javascript/objects-and-arrays-javascript.md)   
 [typeof 運算子](../javascript/reference/typeof-operator-decrementjavascript.md)