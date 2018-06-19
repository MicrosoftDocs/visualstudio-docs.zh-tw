---
title: Promise.reject 函式 （承諾） |Microsoft 文件
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639268"
---
# <a name="promisereject-function-promise"></a>Promise.reject 函式 (承諾)
建立包含等同於傳入引數之結果的新被拒承諾。  
  
## <a name="syntax"></a>語法  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>參數  
 `r`  
 必要項。 承諾被拒的原因。  
  
## <a name="remarks"></a>備註  
 處理當被拒承諾傳回時，執行 `then` 或 `catch` 方法之函數時所發生的錯誤。  
  
## <a name="example"></a>範例  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)