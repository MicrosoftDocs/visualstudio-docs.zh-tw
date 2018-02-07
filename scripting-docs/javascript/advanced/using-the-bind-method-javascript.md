---
title: "使用 bind 方法 (JavaScript) | Microsoft Docs"
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
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d185801cc5bba355751147edb79b9c47d21f8eed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2018
---
# <a name="using-the-bind-method-javascript"></a>使用 bind 方法 (JavaScript)
JavaScript `bind` 方法有數種用途。 通常它是用來保留另一個內容中執行之函式的執行內容。 `bind` 會建立與原始函式擁有相同主體的新函式。 傳遞給 `bind` 的第一個引數會指定繫結函式中 `this` 關鍵字的值。 您也可以將額外的選擇性引數傳遞至 `bind`。 如需其他用法的範例，請參閱 [bind 方法 (函式)](../../javascript/reference/bind-method-function-javascript.md)。 如需使用 `bind` 部分套用函式的範例，請參閱[使用 Hilo JavaScript 的非同步程式設計模式和祕訣 (Windows 市集)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx)。  
  
## <a name="preserving-the-execution-context-using-bind"></a>使用 bind 保留執行內容  
 `bind` 函式通常是在加入事件接聽程式時使用。 在下列程式碼範例中，`bind` 會用來保留目前物件 (`DataObject`) 的內容。 您可以使用 `bind` 關鍵字將資料物件傳遞至 `this`，這樣就能在事件處理常式 (`dataReadyHandler`) 執行時存取資料物件屬性和函式。 下列程式碼會建立自訂事件來示範 `bind` 的運作方式。  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 如果您將使用 `bind` 的程式碼行加上註解，請將呼叫 `addEventListener` 但不使用 `bind` 的程式碼行取消註解，然後重新執行程式碼，則 `dataReadyHandler` 函式將會失敗。 例如，在 `dataReadyHandler` 中，`this.name` 將會是未定義，而且 `this.data()` 會產生錯誤，因為 `this` 物件不再參考資料物件。  
  
## <a name="see-also"></a>請參閱  
 [bind 方法 (Function)](../../javascript/reference/bind-method-function-javascript.md)
