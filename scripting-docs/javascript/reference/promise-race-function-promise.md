---
title: "Promise.race 函式 （承諾） |Microsoft 文件"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d35c448ad143facdcd783df0551505e440521b98
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2018
---
# <a name="promiserace-function-promise"></a>Promise.race 函式 (承諾)
建立可以解析或拒絕結果值與第一個承諾相同的新承諾，以解析或拒絕所傳入的引數。  
  
## <a name="syntax"></a>語法  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>參數  
 `iterable`  
 必要。 一或多個承諾。  
  
## <a name="remarks"></a>備註  
 `iterable` 中如有任何承諾處於已解析或被拒的狀態，`Promise.race` 會以處理結果值等於解析 (或拒絕) 該承諾時所使用的相同方式，傳回已解析或被拒的承諾。 `iterable` 中如有多個承諾已解決或被拒，`Promise.race` 會以第一個反覆執行之承諾的相同方式，傳回已解析的承諾。 如果沒有可以反覆解析或拒絕的承諾，從 `Promise.race` 傳回的承諾也不會加以解析或拒絕。  
  
## <a name="example"></a>範例  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p3 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)
