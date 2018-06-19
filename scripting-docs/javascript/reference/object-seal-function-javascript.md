---
title: Object.seal 函式 (JavaScript) |Microsoft 文件
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
helpviewer_keywords:
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641148"
---
# <a name="objectseal-function-javascript"></a>Object.seal 函式 (JavaScript)
防止修改現有屬性 (Property) 的屬性 (Attribute)，並可防止新屬性  (Attribute) 加入。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 要鎖定的屬性物件。  
  
## <a name="return-value"></a>傳回值  
 傳遞至函式物件。  
  
## <a name="exceptions"></a>例外狀況  
 如果`object`引數不是物件，`TypeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 `Object.seal`函式沒有兩個動作：  
  
-   使物件不可延伸，如此無法加入新的屬性。  
  
-   設定`configurable`屬性`false`物件的所有屬性。  
  
 當`configurable`屬性是`false`，無法變更屬性的屬性，而且無法刪除屬性。 當`configurable`是`false`和`writable`是`true`、`value`和`writable`屬性已變更。  
  
 `Object.seal`函式不會變更`writable`屬性。  
  
 如需如何設定屬性的屬性的詳細資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。 若要取得屬性的屬性，您可以使用[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="related-functions"></a>相關函式  
 下列相關的功能會防止物件屬性修改。  
  
|函式|物件是由非可延伸|`configurable`設定為`false`每一個屬性|`writable`設定為`false`每一個屬性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|否|否|  
|`Object.seal`|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 下列函式會傳回`true`所有標示為下表中的條件時，則為 true。  
  
|函式|物件是可延伸嗎？|`configurable`是`false`所有屬性嗎？|`writable`是`false`所有的資料屬性嗎？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Object.seal` 函式：  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)