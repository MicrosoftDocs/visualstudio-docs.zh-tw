---
title: "管理事件接聽程式 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="managing-event-listeners"></a>管理事件接聽程式
如果 DOM 項目或物件的存留期與其相關聯事件接聽程式的存留期不同，則可能需要使用 [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx) 方法避免記憶體流失。  
  
## <a name="event-listeners-and-object-scope"></a>事件接聽程式和物件範圍  
 下列程式碼範例顯示可能會在呼叫 `dataObjFactory()` 函式時導致記憶體流失的程式碼。 在此程式碼中，每次建立新的資料物件時，都會為資料物件註冊事件接聽程式。 若要在 `dataReady()` 事件處理常式中使用目前資料物件，則會在 `addEventListener` 中使用 [bind 方法 (函式)](../../javascript/reference/bind-method-function-javascript.md)。  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 每個資料物件的接聽程式都是使用 `document` 物件所註冊，而該物件的存留期與資料物件不同。 只要 `document` 物件保持在範圍內，每個資料物件的註冊事件接聽程式就可以防止記憶體回收。  (在一些現代 JavaScript 設計模式中，document 物件會在 Web 應用程式存留期保持在範圍內)。若要防止記憶體流失，會在 `removeEventListener` 函式中呼叫 `dataObjFactory`。 不過，此程式碼會失敗，原因是在 `bind` 函式所傳回之事件處理常式的繫結版本上尚未呼叫 `removeEventListener`。  
  
 若要修正此程式碼，並且讓資料物件可以進行記憶體回收，您必須先儲存事件處理常式之繫結版本的參考 (如此程式碼所示)，然後將儲存的參考傳遞給 `addEventListener`。 `DataObject` 的更正程式碼如下：  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 最後，您需要在繫結函式的已儲存參考 (`removeEventListener`) 上呼叫 `handlerRef`。 `dataObjFactory` 的更正程式碼如下：  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 現在，`removeEventListener` 呼叫會運作，並將不需要的資料物件進行記憶體回收，即使 `document` 物件保持在範圍中也是一樣。