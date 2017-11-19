---
title: "Object.isSealed 函式 (JavaScript) |Microsoft 文件"
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
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectissealed-function-javascript"></a>Object.isSealed 函式 (JavaScript)
如果無法在物件中修改現有屬性 (Property) 的屬性 (Attribute)，且新的屬性 (Property) 無法加入物件，便傳回 `true`。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 要測試的物件。  
  
## <a name="return-value"></a>傳回值  
 `true`如果這兩個下列條件：  
  
-   此物件是不可延伸表示的物件，無法加入新的屬性。  
  
-   `configurable`屬性是`false`所有現有的屬性。  
  
 如果物件沒有任何屬性，則此函數會傳回`true`如果物件是不可延伸。  
  
## <a name="exceptions"></a>例外狀況  
 如果`object`引數不是物件，`TypeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 當`configurable`屬性的屬性是`false`，無法變更該屬性的屬性，而且無法刪除屬性。 當`writable`是`false`，無法變更資料屬性值。 當`configurable`是`false`和`writable`是`true`、`value`和`writable`屬性已變更。  
  
 `Object.isSealed`函式不會使用`writable`屬性，以便判斷它的傳回值的屬性。  
  
 如需如何設定屬性的屬性資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。 若要取得屬性的屬性，您可以使用[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="related-functions"></a>相關函式  
 下列相關的功能會防止物件屬性修改。  
  
|函式|物件是由非可延伸|`configurable`設定為`false`每一個屬性|`writable`設定為`false`每一個屬性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 下列函式會傳回`true`所有標示為下表中的條件時，則為 true。  
  
|函式|物件是可延伸嗎？|`configurable`是`false`所有屬性嗎？|`writable`是`false`所有的資料屬性嗎？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|`Object.isSealed`|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Object.isSealed` 函式：  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)