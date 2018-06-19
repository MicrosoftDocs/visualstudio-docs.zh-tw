---
title: Object.freeze 函式 (JavaScript) |Microsoft 文件
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641818"
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze 函式 (JavaScript)
防止修改現有屬性 (Property) 的屬性 (Attribute) 和值，並可防止新屬性 (Property) 加入。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 要鎖定的屬性物件。  
  
## <a name="return-value"></a>傳回值  
 傳遞至函式物件。  
  
## <a name="exceptions"></a>例外狀況  
 如果`object`引數不是物件，`TypeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 `Object.freeze`函式會執行下列：  
  
-   使物件不可延伸，如此無法加入新的屬性。  
  
-   設定`configurable`屬性`false`物件的所有屬性。 當`configurable`是`false`，無法變更該屬性的屬性，而且無法刪除屬性。  
  
-   設定`writable`屬性`false`所有的資料內容的物件。 當`writable`為 false，無法變更資料屬性值。  
  
 如需如何設定屬性的屬性的詳細資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。 若要取得屬性的屬性，您可以使用[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="related-functions"></a>相關函式  
 下列相關的功能會防止物件屬性修改。  
  
|函式|物件是由非可延伸|`configurable`設定為`false`每一個屬性|`writable`設定為`false`每一個屬性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|`Object.freeze`|是|是|是|  
  
 下列函式會傳回`true`所有標示為下表中的條件時，則為 true。  
  
|函式|物件是可延伸嗎？|`configurable`是`false`所有屬性嗎？|`writable`是`false`所有的資料屬性嗎？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|是|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## <a name="example"></a>範例  
 下面範例說明如何使用 `Object.freeze` 函式：  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)