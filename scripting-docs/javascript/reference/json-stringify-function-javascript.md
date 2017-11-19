---
title: "JSON.stringify 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsonstringify-function-javascript"></a>JSON.stringify 函式 (JavaScript)
將 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值轉換成以 JavaScript 物件標記法 (JavaScript Object Notation，JSON) 表示的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>參數  
 `value`  
 必要項。 要轉換的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值，這個值通常是物件或陣列。  
  
 `replacer`  
 選擇項。 用來轉換結果的函式或陣列。  
  
 如果 `replacer` 是函式，則 `JSON.stringify` 會呼叫函式，並傳入每個成員的索引鍵和值， 並使用傳回值而不是原始值。 如果函式傳回 `undefined`，就表示已排除這個成員。 根物件的索引鍵是空字串：""。  
  
 如果 `replacer` 是陣列，則只會轉換陣列中有索引鍵值的成員。 成員的轉換順序與陣列中索引鍵的順序相同。 如果 `replacer` 引數也是陣列，則轉換時便會忽略 `value` 陣列。  
  
 `space`  
 選擇項。 加入縮排、空白字元和分行符號字元，讓傳回值 JSON 文字更容易閱讀。  
  
 如果省略 `space`，產生的傳回值文字就不會包含任何額外的空白字元。  
  
 如果 `space` 是數字，傳回值文字在每個階層都會使用指定的空白字元數目進行縮排。 如果 `space` 大於 10，文字只會使用 10 個空白字元進行縮排。  
  
 如果 `space` 是非空白字串 (例如 '\t')，則傳回值文字會在每個階層使用該字串中的字元進行縮排。  
  
 如果 `space` 是長度超過 10 個字元的字串，則只會使用前 10 個字元。  
  
## <a name="return-value"></a>傳回值  
 包含 JSON 文字的字串。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況|條件|  
|---------------|---------------|  
|[無效的取代子引數](../../javascript/misc/invalid-replacer-argument.md)|`replacer` 引數不是函式或陣列。|  
|[不支援數值引數中的循環參考](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|`value` 引數包含循環參考。|  
  
## <a name="remarks"></a>備註  
 如果 `value` 具有 `toJSON` 方法，`JSON.stringify` 函式會使用該方法的傳回值。 如果 `toJSON` 方法的傳回值是 `undefined`，就不會轉換這個成員。 如此一來，物件就能判斷自己專屬的 JSON 表示方式。  
  
 對於沒有 JSON 表示方式的值 (例如 `undefined`)，就不會轉換這些值。 在物件中，這些值會遭到捨棄。 在陣列中，這些值會以 null 取代。  
  
 字串值的開頭和結尾都必須加上引號， 除了必須使用反斜線逸出的字元之外，所有 Unicode 字元前後都可以加上引號。 下列字元前面必須加上反斜線：  
  
-   引號 (")  
  
-   反斜線 (\\)  
  
-   退格鍵 (b)  
  
-   換頁字元 (f)  
  
-   新行字元 (n)  
  
-   歸位字元 (r)  
  
-   水平定位字元 (t)  
  
-   四個十六進位數字 (uhhhh)  
  
## <a name="order-of-execution"></a>執行的順序  
 在序列化程序中，如果 `toJSON` 引數具有 `value` 方法，`JSON.stringify` 會先呼叫 `toJSON` 方法。 如果該方法不存在，則會使用原始值。 接下來，如果有提供 `replacer` 引數，就會以 `toJSON` 引數的傳回值取代原始值或 `replacer` 的傳回值。 最後會根據選擇性的 `space` 引數在值中加入空白字元，以產生最終的 JSON 文字。  
  
## <a name="example"></a>範例  
 下列範例會使用 `JSON.stringify` 將 `contact` 物件轉換成 JSON 文字。 由於範例中已定義 `memberfilter` 陣列，所以只會轉換 `surname` 和 `phone` 成員。 `firstname` 成員將會省略。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>範例  
 下列範例會使用 `JSON.stringify` 搭配陣列。 `replaceToUpper` 函式會將陣列中的每個字串轉換成大寫。  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>範例  
 下列範例會使用 `toJSON` 方法，將字串值轉換成大寫。  
  
```JavaScript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON 方法 （日期）](../../javascript/reference/tojson-method-date-javascript.md)   
 [摘要讀取器的範例應用程式 （Windows 市集）](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)