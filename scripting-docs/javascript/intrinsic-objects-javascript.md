---
title: 內建物件 (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569608"
---
# <a name="intrinsic-objects-javascript"></a>內建物件 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 提供內建物件。 它們是 `Array`、`Boolean`、`Date`、`Error`、`Function`、**Global**、**JSON**、**Math**、**Number**、`Object`、`RegExp` 和 `String` 物件。 內建物件具有[語言參考](../javascript/reference/javascript-reference.md)中詳述的相關聯方法、函式、屬性和常數。  
  
## <a name="array-object"></a>Array 物件  
 陣列的註標可視為物件的屬性，而且依其數值索引進行參考。 請注意，無法根據數字，對加入陣列的具名屬性進行編製索引；它們與陣列項目不同。  
  
 若要建立新的陣列，請使用 **new** 運算子和 **Array()** [建構函式](../javascript/reference/constructor-property-object-javascript.md)，如下列範例所示。  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 使用 `Array` 關鍵字建立陣列時，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 包括可記錄項目數的 **length** 屬性。 如果未指定數字，則長度設定為 0，而且陣列沒有項目。 如果指定數字，則長度會設定為該數字。 如果指定多個參數，則會使用參數做為陣列中的項目。 此外，還會將參數數目指派給 length 屬性 (如下列範例所示)，這等同於先前的範例所示。  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會在將項目新增至您使用 `Array` 關鍵字所建立的陣列時自動變更 **length** 的值。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的陣列索引一律從 0 開始，不是 1，讓 length 屬性一律比陣列中的最大索引大一。  
  
## <a name="string-object"></a>String 物件  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，您可以將字串 (和數字) 視為物件。 [string 物件](../javascript/reference/string-object-javascript.md)具有可與字串搭配使用的特定內建方法。 其中一個是可傳回部分字串的 [substring 方法](../javascript/reference/substring-method-string-javascript.md)。 它使用兩個數字做為其引數。  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 `String` 物件的另一個屬性是 **length** 屬性。 此屬性包含字串 (0 為空字串) 中的字元數。 這是數值，可直接用於計算。  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Math 物件  
 **Math** 物件有許多預先定義的常數和函式。 常數是特定數字。 其中一個特定數字是 pi 的值 (大約是 3.14159...)。這是 **Math.PI** 常數 (如下列範例所示)。  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 **Math** 物件的其中一個內建函式是乘冪方法或 `Math.pow` (會讓數字成為指定的次方)。 下列範例同時使用 pi 和乘冪來計算球體的容量。  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Date 物件  
 `Date` 物件可以用來代表任意日期和時間、取得目前的系統日期，以及計算日期之間的差異。 它具有數個屬性和方法 (全部都是預先定義的)。 一般而言，`Date` 物件提供星期幾、月份、日期和年份，以及以小時、分鐘和秒為單位的時間。 這項資訊是根據 1970 年 1 月 1 日 00:00:00.000 GMT 開始算起的毫秒數，也就是格林威治標準時間 (慣用的詞彙是 UTC 或「全球定位時間」，其指的是世界時間標準所發出的訊號)。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 可以處理落在西元前 250,000 與西元 255,000 之大約範圍內的日期。  
  
 若要建立新的 `Date` 物件，請使用 **new** 運算子 (如下列範例所示)。  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Number 物件  
 除了 **Math** 物件中可用的特殊數值常數 (例如，`PI`) 之外，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中還透過 **Number** 物件提供數個其他常數。  
  
|常數|描述|  
|--------------|-----------------|  
|Number.MAX_VALUE|最大可能數字 (約 1.79E+308)；可以是正數或負數。 (值會根據系統而略有不同。)|  
|Number.MIN_VALUE|最小可能數字 (約 5.00E-324)；可以是正數或負數。 (值會根據系統而略有不同。)|  
|Number.NaN|特殊非數值，「不是數字」。|  
|Number.POSITIVE_INFINITY|任何大於最大正數 (Number.MAX_VALUE) 的正值會自動轉換成此值；呈現為 infinity。|  
|Number.NEGATIVE_INFINITY|任何負值超過最大負數 (-Number.MAX_VALUE) 的值會自動轉換成此值；呈現為 -infinity。|  
  
 **Number.NaN** 是定義為「不是數字」的特殊常數。 嘗試剖析無法剖析為數字的字串時傳回 **Number.NaN**。 `NaN` 與任何數字和本身比較，但不相等。 若要測試 `NaN` 結果，請不要比較 **Number.NaN**；請改用 **isNaN()** 函式。  
  
## <a name="json-object"></a>JSON 物件  
 JSON 是精簡型資料交換格式，並以 JavaScript 語言之物件常值標記法的子集為基礎。  
  
 JSON 物件提供兩個函式，可轉換成 JSON 文字格式或從中進行轉換。 [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) 函式會將物件和陣列序列化為 JSON 文字。 [JSON.parse](../javascript/reference/json-parse-function-javascript.md) 函式會取消序列化 JSON 文字，以產生記憶體中的物件。 如需詳細資訊，請參閱 [JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](http://go.microsoft.com/fwlink/?LinkId=124098)。  
  
## <a name="see-also"></a>另請參閱  
 [JavaScript 物件](../javascript/reference/javascript-objects.md)