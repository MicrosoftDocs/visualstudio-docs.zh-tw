---
title: Promise 物件 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61e5611dd0d455c7e7b704777cc2341ca43a2404
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640628"
---
# <a name="promise-object-javascript"></a>Promise 物件 (JavaScript)
提供一個機制來排程對尚未計算的值進行的工作。 它是管理與非同步 API 互動的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### <a name="parameters"></a>參數  
 `promise`  
 必要項。 要對其指派承諾的變數名稱。  
  
 `resolve`  
 必要項。 執行以表示承諾已順利完成的函式。  
  
 `reject`  
 選擇項。 執行以表示已拒絕承諾並發生錯誤的函式。  
  
## <a name="remarks"></a>備註  
 承諾必須完成並具有值，或必須有原因的拒絕。 完成或拒絕 (視何者先發生) 承諾時，會執行 Promise 物件的 `then` 方法。 如果承諾順利完成，則會執行 `then` 方法的履行處理常式函式。 如果已拒絕承諾，則會執行 `then` 方法 (或 `catch` 方法) 的錯誤處理常式函式。  
  
## <a name="example"></a>範例  
 下列範例示範如何呼叫會傳回承諾的函式 (`timeout`)。 在 5000 毫秒逾時到期之後，會執行 `then` 方法的履行處理常式。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="example"></a>範例  
 您也可以鏈結 `then` 方法的呼叫，如下列程式碼所示。 每個完成處理常式本身都必須傳回承諾，以支援鏈結。 在此程式碼 (呼叫相同的 `timeout` 函式) 中，會在 1000 毫秒之後傳回逾時的第一個呼叫。 第一個完成處理常式會再次呼叫 `timeout`，並在 2000 毫秒之後傳回這個承諾。 它的完成處理常式之後會擲回錯誤。 只有在完成或拒絕兩個逾時呼叫時，錯誤處理常式才會呼叫 `Promise.all`。  
  
```JavaScript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="functions"></a>函式  
 下表描述 `Promise` 物件的函式。  
  
|函式|說明|  
|--------------|-----------------|  
|[Promise.all 函式](../../javascript/reference/promise-all-function-promise.md)|聯結兩個以上的承諾，而且只有在完成或拒絕所有指定的承諾時才會傳回。|  
|[Promise.race 函式](../../javascript/reference/promise-race-function-promise.md)|建立可以解析或拒絕結果值與第一個承諾相同的新承諾，以解析或拒絕所傳入的引數。|  
|[Promise.reject 函式](../../javascript/reference/promise-reject-function-promise.md)|建立包含等同於傳入引數之結果的新被拒承諾。|  
|[Promise.resolve 函式](../../javascript/reference/promise-resolve-function-promise.md)|建立新的已解析承諾，其結果等同於其引數。|  
  
## <a name="methods"></a>方法  
 下表描述 `Promise` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[catch 方法](../../javascript/reference/catch-method-promise.md)|可讓您指定要對拒絕承諾進行的工作。|  
|[then 方法](../../javascript/reference/then-method-promise.md)|可讓您指定要對履行承諾進行的工作。|