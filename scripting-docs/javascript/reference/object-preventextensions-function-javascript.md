---
title: "Object.preventExtensions 函式 (JavaScript) |Microsoft 文件"
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
helpviewer_keywords:
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectpreventextensions-function-javascript"></a>Object.preventExtensions 函式 (JavaScript)
防止新屬性加入物件。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 要變成不可延伸的物件。  
  
## <a name="return-value"></a>傳回值  
 傳遞至函式物件。  
  
## <a name="exceptions"></a>例外狀況  
 如果`object`引數不是物件，`TypeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 `Object.preventExtensions`函式將物件不可延伸，因此無法加入新的具名的屬性。 建立非可延伸物件之後，它無法進行可延伸。  
  
 如需如何設定屬性的屬性資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## <a name="related-functions"></a>相關函式  
 下列相關的功能會防止物件屬性修改。  
  
|函式|物件是由非可延伸|`configurable`設定為`false`每一個屬性|`writable`設定為`false`每一個屬性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 下列函式會傳回`true`所有標示為下表中的條件時，則為 true。  
  
|函式|物件是可延伸嗎？|`configurable`是`false`所有屬性嗎？|`writable`是`false`所有的資料屬性嗎？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Object.preventExtensions` 函式：  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)