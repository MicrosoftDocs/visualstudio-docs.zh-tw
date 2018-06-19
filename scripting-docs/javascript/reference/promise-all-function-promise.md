---
title: Promise.all 函式 （承諾） |Microsoft 文件
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639908"
---
# <a name="promiseall-function-promise"></a>Promise.all 函式 (承諾)
聯結兩個以上的承諾，而且只有在完成或拒絕所有指定的承諾時才會傳回。  
  
## <a name="syntax"></a>語法  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>參數  
 `func1`  
 必要項。 傳回承諾的函式。  
  
 `func2`  
 必要項。 傳回承諾的函式。  
  
 `funcN`  
 選擇項。 傳回承諾的一或多個函式。  
  
## <a name="remarks"></a>備註  
 傳回的結果是一個值陣列，這些值是由完成的承諾所傳回。 如果其中一個聯結承諾遭到拒絕，`Promise.all` 立即和遭拒承諾原因一起傳回 (所有其他傳回值都會被捨棄)。  
  
## <a name="example"></a>範例  
 在這段程式碼中，第一個逾時呼叫會在 5000 毫秒後傳回。 只有兩個逾時呼叫都完成或拒絕時，完成處理常式才會呼叫 `Promise.all`。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)