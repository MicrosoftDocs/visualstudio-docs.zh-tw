---
title: "Object.create 函式 (JavaScript) |Microsoft 文件"
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectcreate-function-javascript"></a>Object.create 函式 (JavaScript)
建立具有指定的原型，並選擇性地包含指定之屬性的物件。  
  
## <a name="syntax"></a>語法  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>參數  
 `prototype`  
 必要項。 要做為原型的物件。 可以是 `null`。  
  
 `descriptors`  
 選擇項。 A[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件，其中包含一或多個屬性描述項。  
  
 「資料屬性」是可取得和設定值的屬性。 包含資料的屬性描述元`value`屬性，加上`writable`， `enumerable`，和`configurable`屬性。 如果未指定的最後三個屬性，其預設`false`。 *存取子屬性*呼叫使用者提供函式，每次擷取或設定值。 存取子屬性描述元包含`set`屬性`get`屬性，或兩者。 如需詳細資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## <a name="return-value"></a>傳回值  
 新的物件具有指定的內部原型，並包含指定的內容，如果有的話。  
  
## <a name="exceptions"></a>例外狀況  
 A`TypeError`如果下列任何一個狀況成立，會擲回例外狀況：  
  
-   `prototype`引數不是物件，並不是`null`。  
  
-   中的描述元`descriptors`引數必須具有`value`或`writable`屬性，且具有`get`或`set`屬性。  
  
-   中的描述元`descriptors`引數必須具有`get`或`set`不是函式的屬性。  
  
## <a name="remarks"></a>備註  
 您可以使用這個函式使用`null``prototype`參數，以停止的原型鏈結。 建立的物件會有任何原型。  
  
## <a name="example"></a>範例  
 下列範例會建立物件使用`null`原型，並將兩個可列舉屬性。  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>範例  
 下列範例會建立具有相同的內部原型為物件的物件。 您可以看到它具有的相同原型為使用物件常值所建立的物件。 [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)函式會取得原始物件的原型。 若要取得物件的屬性描述元，您可以使用[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>範例  
 下列範例會建立具有相同的內部原型為圖形物件的物件。  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf 方法 (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [建立物件](../../javascript/creating-objects-javascript.md)