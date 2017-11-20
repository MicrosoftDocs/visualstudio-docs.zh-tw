---
title: "Promise.resolve 函式 （承諾） |Microsoft 文件"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="promiseresolve-function-promise"></a>Promise.resolve 函式 (承諾)
建立新的已解析承諾，其結果等同於其引數。  
  
## <a name="syntax"></a>語法  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 必要項。 隨已完成的承諾傳回的值。  
  
## <a name="remarks"></a>備註  
 傳回已完成的 Promise 物件時，即會執行`then` 方法的履行處理函式。  
  
## <a name="example"></a>範例  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)