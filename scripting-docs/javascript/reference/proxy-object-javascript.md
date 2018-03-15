---
title: "Proxy 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="proxy-object-javascript"></a>Proxy 物件 (JavaScript)
啟用物件的自訂行為。  
  
## <a name="syntax"></a>語法  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>參數  
 `target`  
 必要。 Proxy 所要虛擬化的物件或函式。  
  
 `handler`  
 必要。 使用方法 (設陷) 來實作自訂行為的物件。  
  
## <a name="remarks"></a>備註  
 `Proxy` 物件可用來攔截另一個物件上的內部低階作業。 Proxy 物件可用於攔截、物件虛擬化、記錄/分析和其他用途。  
  
 如果未在 Proxy 的處理常式中定義特定作業的設陷，作業會轉送至目標。  
  
 事件處理常式物件會定義下列方法 (設陷)，來實作自訂行為。 此處的範例並不詳盡。 若要支援條件式預設行為的處理常式方法中，使用方法[反映物件](../../javascript/reference/reflect-object-javascript.md)。  
  
|處理常式方法 (設陷) 語法|使用範例|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|函式呼叫的設陷。|  
|`construct: function(target, args)`|建構函式的設陷。|  
|`defineProperty: function(target, propertyName, descriptor)`|設陷[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。|  
|`deleteProperty: function(target, propertyName)`|`delete` 陳述式的設陷。|  
|`enumerate: function(target)`|設陷[for...in..中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)陳述式， [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)， [Object.keys](../../javascript/reference/object-keys-function-javascript.md)函式，和[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)。|  
|`get: function(target, propertyName, receiver)`|任何的設陷[getter](../../javascript/creating-objects-javascript.md)屬性。|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|設陷[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。|  
|`getPrototypeOf: function(target)`|設陷[Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)。|  
|`has: function(target, propertyName)`|設陷`in`運算子， [hasOwnProperty 方法 (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)，和其他方法。|  
|`isExtensible: function(target)`|設陷[Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)。|  
|`ownKeys: function(target)`|設陷[Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)。|  
|`preventExtensions: function(target)`|設陷[Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)。|  
|`set: function(target, propertyName, value, receiver)`|任何的設陷[setter](../../javascript/creating-objects-javascript.md)屬性。|  
|`setPrototypeOf: function(target, prototype)`|設陷[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)。|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `get` 設陷建立物件常值的 Proxy。  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 `apply` 設陷建立函式的 Proxy。  
  
```JavaScript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
