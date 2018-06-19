---
title: JSON.parse 函式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- JSON.parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse JSON method
- JSON.parse method
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 519fc733fd42a194fbd7335127ddf9bcf0bdc220
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2018
ms.locfileid: "27782187"
---
# <a name="jsonparse-function-javascript"></a>JSON.parse 函式 (JavaScript)
將以 JavaScript 物件標記法 (JavaScript Object Notation，JSON) 表示的字串轉換成物件。  
  
## <a name="syntax"></a>語法  
  
```  
JSON.parse(text [, reviver])  
```  
  
## <a name="parameters"></a>參數  
 `text`  
 必要項。 有效的 JSON 字串。  
  
 `reviver`  
 選擇項。 用來轉換結果的函式。 呼叫這個函式時，會針對這個物件的每個成員進行呼叫。 如果成員包含巢狀物件，則會先轉換巢狀物件，然後再轉換父物件。 就個別成員而言，發生的情況如下：  
  
-   如果 `reviver` 傳回有效值，轉換後的值會取代成員值。  
  
-   如果 `reviver` 的傳回值與它接收的值相同，則不會修改成員值。  
  
-   如果 `reviver` 傳回 `null` 或 `undefined`，表示成員已刪除。  
  
## <a name="return-value"></a>傳回值  
 物件或陣列。  
  
## <a name="exceptions"></a>例外狀況  
 如果這個函式導致 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 剖析器錯誤 (例如「SCRIPT1014：無效的字元」)，表示輸入的文字不符合 JSON 語法。 若要修正錯誤，請執行下列一項動作：  
  
-   修改 `text` 引數，使其符合 JSON 語法。 如需詳細資訊，請參閱 JSON 物件的 [BNF 語法標記法](http://go.microsoft.com/fwlink/?LinkId=125203) 。  
  
     例如，如果回應採用 JSONP 格式而不是純 JSON，請在回應物件上嘗試此程式碼：  
  
    ```JavaScript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   請確定已透過 JSON 相容實作 (例如 `text` ) 來序列化 `JSON.stringify`引數。  
  
-   執行`text`引數，在 JSON 驗證程式，例如[JSLint](http://www.jslint.com/)或[JSON，將 CSV](https://json-csv.com)來協助識別語法錯誤。  
  
## <a name="example"></a>範例  
 下面範例會使用 `JSON.parse` 將 JSON 字串轉換為物件。  
  
```JavaScript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## <a name="example"></a>範例  
 下面範例會使用 `JSON.stringify`將陣列轉換為 JSON 字串，然後使用 `JSON.parse`將字串轉換回陣列。  
  
```JavaScript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## <a name="example"></a>範例  
 `reviver` 函式通常是用來將以 JSON 字串表示的「國際標準組織」(International Organization for Standardization，ISO) 日期字串轉換成具有「國際標準時間」(Coordinated Universal Time，UTC) 格式的 `Date` 物件。 下面這個範例會使用 `JSON.parse` 還原序列化具有 ISO 格式的日期字串。 `dateReviver` 函式會針對格式如同 ISO 日期字串格式的成員傳回 `Date` 物件。  
  
```JavaScript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [JSON.stringify 函式](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON 方法 （日期）](../../javascript/reference/tojson-method-date-javascript.md)   
 [中樞範本範例應用程式 （Windows 市集）](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)