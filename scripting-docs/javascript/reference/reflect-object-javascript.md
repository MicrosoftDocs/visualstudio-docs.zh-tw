---
title: Reflect 物件 (JavaScript) |Microsoft 文件
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640918"
---
# <a name="reflect-object-javascript"></a>Reflect 物件 (JavaScript)
提供用於攔截作業的方法。  
  
## <a name="syntax"></a>語法  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>參數  
 `method`  
 必要項。 `Reflect` 物件的其中一個方法名稱。  
  
## <a name="remarks"></a>備註  
 反射物件無法使用 `new` 運算子具現化。  
  
 反映的方法通常會搭配使用[proxy](../../javascript/reference/proxy-object-javascript.md) ，因為它允許您委派預設行為，但不用在程式碼中實作預設行為。  
  
 反射提供的靜態方法，和每個 Proxy 設陷具有相同的名稱。 資料表中的說明並不詳盡。  
  
|方法|說明|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|類似於[套用](../../javascript/reference/apply-method-function-javascript.md)函式物件的方法。|  
|`Reflect.construct(target, args)`|`new` 運算子的對等函式。|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|類似於[Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)。 傳回布林值，指出呼叫是否成功。|  
|`Reflect.deleteProperty(target, propertyName)`|類似於 `delete` 陳述式。 傳回布林值，指出呼叫是否成功。|  
|`Reflect.enumerate(target)`|類似於[for...in..中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)陳述式， [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)， [Object.keys](../../javascript/reference/object-keys-function-javascript.md)函式，和[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)。|  
|`Reflect.get(target, propertyName, receiver)`|任何對等函式[getter](../../javascript/creating-objects-javascript.md)屬性。|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|類似於[Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。 傳回布林值，指出呼叫是否成功。|  
|`Reflect.getPrototypeOf(target)`|類似於[Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)。|  
|`Reflect.has(target, propertyName)`|類似於`in`運算子， [hasOwnProperty 方法 (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)，和其他方法。 傳回布林值，指出呼叫是否成功。|  
|`Reflect.isExtensible(target)`|類似於[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)。|  
|`Reflect.ownKeys(target)`|類似於[Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)。|  
|`Reflect.preventExtensions(target)`|類似於[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)。 傳回布林值，指出呼叫是否成功。|  
|`Reflect.set(target, propertyName, value, receiver)`|類似於使用任何[setter](../../javascript/creating-objects-javascript.md)屬性。 傳回布林值，指出呼叫是否成功。|  
|`Reflect.setPrototypeOf(target, prototype)`|類似於[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)。 傳回布林值，指出呼叫是否成功。|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `Reflect.get` 寫入 Proxy，它會封鎖取得作業，使其無法取得以底線開頭的屬性。  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]