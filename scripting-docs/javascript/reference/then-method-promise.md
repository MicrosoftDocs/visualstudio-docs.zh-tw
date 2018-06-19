---
title: then 方法 （承諾） |Microsoft 文件
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640208"
---
# <a name="then-method-promise"></a>then 方法 (承諾)
可讓您指定要對履行承諾進行的工作。  
  
## <a name="syntax"></a>語法  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>參數  
 `promise`  
 必要項。 Promise 物件  
  
 `onCompleted`  
 必要項。 承諾順利完成時要執行的「履行」處理常式函式。  
  
 `onRejected`  
 選擇項。 要在拒絕承諾時執行的錯誤處理常式函式。  
  
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
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)