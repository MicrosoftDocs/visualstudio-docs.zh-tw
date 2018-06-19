---
title: 迭代器和產生器 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a566e870c6e9589daed86d42e3fb933374cbb17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977266"
---
# <a name="iterators-and-generators-javascript"></a>迭代器和產生器 (JavaScript)
迭代器是用來周遊容器物件 (例如清單) 的物件。 在 JavaScript 中，迭代器物件不是不同的內建物件，而是實作 `next` 方法來存取容器物件中下一個項目的物件。  
  
 在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中，您可以建立自己的自訂迭代器。 不過，使用產生器通常較為容易，可大幅簡化迭代器的建立。 產生器是一種函式類型，其為迭代器的處理站。 若要使用產生器函式來建立自訂迭代器，請參閱[產生器](#Generators)。  
  
> [!CAUTION]
>  [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] 支援產生器。  
  
## <a name="iterators"></a>迭代器  
 JavaScript 迭代器的實作包含兩個或三個符合特定介面的物件：  
  
-   Iterable 介面  
  
-   Iterator 介面  
  
-   IteratorResult 介面  
  
 使用這些介面，即可建立自訂迭代器。 這可讓您使用 `for…of` 陳述式來周遊可反覆執行的物件。  
  
### <a name="iterable-interface"></a>Iterable 介面  
 Iterable 介面是可反覆執行的物件 (可取得迭代器的物件) 所需的介面。 例如，`for (let e of C)` 中的 `C` 必須實作 Iterable 介面。  
  
 可反覆執行的物件必須提供傳回迭代器的 Symbol.iterator 方法。  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 這個屬性必須是未接受引數且傳回物件 (`iterObject`) 的函式，而物件符合 `Iterator` 介面。  
  
 許多內建類型 (包括陣列) 現在是可反覆執行的。 `for…of` 迴圈使用可反覆執行的物件。 (不過，並非所有內建可反覆執行的物件都是迭代器。 例如，Array 物件不是迭代器本身，但是可反覆執行的，而 ArrayIterator 也是可反覆執行的。)  
  
### <a name="iterator-interface"></a>Iterator 介面  
 Symbol.iterator 方法所傳回的物件必須實作 `next` 方法。 `next` 方法具有下列語法。  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 `next` 方法是傳回值的函式。 此函式傳回符合 `IteratorResult` 介面的物件 (`iterResultObj`)。 如果迭代器之 `next` 方法的前一個呼叫傳回 `IteratorResult` 物件 (其 `done` 屬性為 true)，則會終止反覆項目，而且不再呼叫 `next` 方法。  
  
 迭代器也可能包括 `return` 方法，確保使用迭代器完成指令碼時已適當地處置迭代器。  
  
### <a name="iteratorresult-interface"></a>IteratorResult 介面  
 IteratorResult 介面是迭代器上 `next` 方法之結果的必要介面。 `next` 所傳回的物件必須提供 `done` 和 `value` 屬性。  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 `done` 屬性會傳回迭代器 `next` 方法呼叫的狀態 (true 或 false)。 如果已達迭代器結尾，則 `done` 會傳回 true。 如果未達結尾，則 `done` 會傳回 false，而且具有值。 如果 `done` 屬性 (它自己或繼承的屬性) 不存在，則會將 `done` 的結果視為 false。  
  
 如果 `done` 是 false，則 `value` 屬性會傳回目前的反覆項目值。 如果 `done` 是 true，則這是迭代器的傳回值 (如果提供傳回值)。 如果迭代器沒有傳回值，則未定義 `value`。 在此情況下，`value` 屬性若未繼承明確值屬性，則可能不是一致物件。  
  
<a name="Generators"></a>   
## <a name="generators"></a>產生器  
 若要輕鬆地建立和使用自訂迭代器，請使用函式* 語法以及一或多個 `yield` 運算式來建立產生器函式。 產生器函式會傳回執行產生器函式主體的迭代器 (即產生器)。 此函式會執行到下一個 `yield` 或 `return` 陳述式。  
  
 呼叫迭代器的 `next` 方法，以從產生器函式傳回下一個值。  
  
 下列範例示範傳回字串物件之迭代器的產生器。  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 在產生器中，yield 運算元運算式會終止 `next` 呼叫，並傳回具有下列兩個屬性的 `IteratorResult` 物件：`done` (`done=false`) 和 `value` (`value=operand`)。 `operand` 是選擇性的，如果缺少，則未定義其值。  
  
 在產生器中，`return` 陳述式會透過下列方式終止產生器：傳回具有 `done=true` 的 `IteratorResult` 以及 value 屬性的選擇性運算元結果。  
  
 您也可以使用 `yield*` 運算式取代 `yield`，以委派給另一個產生器或另一個可反覆執行的物件 (例如陣列或字串)。  
  
 如果您將下列程式碼附加至上述範例，則 `yield*` 會委派給 `stringIter` 產生器。  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 傳遞 `next` 的引數，以及使用引數來修改產生器狀態，也可以建立更進階的產生器。 `next` 會變成先前執行之 `yield` 運算式的結果值。 在下列範例中，將值 100 傳遞給 `next` 方法時，請重設產生器的內部索引值。  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx < str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 其他進階產生器可能會呼叫產生器的 `throw` 方法。 似乎會在暫停產生器 (在下一個 `yield` 陳述式之前) 時擲回所擲回的錯誤。
