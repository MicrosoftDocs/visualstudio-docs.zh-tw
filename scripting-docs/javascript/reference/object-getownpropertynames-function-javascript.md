---
title: Object.getOwnPropertyNames 函式 (JavaScript) |Microsoft 文件
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639928"
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames 函式 (JavaScript)
傳回物件本身屬性的名稱。 物件的自己的屬性是指定義直接於該物件，而且不繼承自物件的原型。 物件的屬性包括欄位 （物件） 和函式。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`object`|必要項。 物件，其中包含自己的屬性。|  
  
## <a name="return-value"></a>傳回值  
 陣列，其中包含自己的屬性物件的名稱。  
  
## <a name="exceptions"></a>例外狀況  
 如果值提供給`object`引數不是物件的名稱，`TypeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 `getOwnPropertyNames`方法會傳回可列舉和非可列舉屬性及方法的名稱。 若要傳回可列舉的屬性及方法的名稱，您可以使用[Object.keys 函式](../../javascript/reference/object-keys-function-javascript.md)。  
  
## <a name="example"></a>範例  
 下列範例會建立具有三個屬性和方法的物件。 然後它會使用`getOwnPropertyNames`方法，以取得物件的屬性 （包括方法）。  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>範例  
 下列範例會顯示以字母為開頭的屬性名稱 ' 中**雜亂無章**物件以建構**義大利麵**建構函式。  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Object.keys 函式](../../javascript/reference/object-keys-function-javascript.md)