---
title: Object.keys 函式 (JavaScript) |Microsoft 文件
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639748"
---
# <a name="objectkeys-function-javascript"></a>Object.keys 函式 (JavaScript)
傳回可列舉屬性的名稱和物件的方法。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|定義|  
|---------------|----------------|  
|`object`|必要項。 包含的屬性和方法的物件。 這可以是您所建立的物件或現有的文件物件模型 (DOM) 物件。|  
  
## <a name="return-value"></a>傳回值  
 陣列，其中包含的可列舉屬性的名稱和物件的方法。  
  
## <a name="exceptions"></a>例外狀況  
 如果值提供給`object`引數不是物件的名稱，`TypeError`擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 `keys`方法會傳回可列舉的屬性及方法的名稱。 若要傳回的可列舉和非可列舉的屬性和方法名稱，您可以使用[Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)。  
  
 如需有關資訊`enumerable`屬性的屬性，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)和[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="example"></a>範例  
 下列範例會建立具有三個屬性和方法的物件。 然後它會使用`keys`方法來取得的屬性和方法的物件。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>範例  
 下列範例會顯示所有開頭字母"g"義大利麵物件中的可列舉屬性的名稱。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)