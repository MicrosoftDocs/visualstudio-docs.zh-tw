---
title: Object.defineProperties 函式 (JavaScript) |Microsoft 文件
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
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640668"
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties 函式 (JavaScript)
將一或多個屬性加入至物件，及/或修改現有屬性 (Property) 的屬性 (Attribute)。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>參數  
 `object`  
 必要項。 要加入或修改的屬性物件。 這可以是原生[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件或 DOM 物件。  
  
 `descriptors`  
 必要項。 A[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件，其中包含一或多個描述元物件。 每個描述元物件會描述資料屬性或存取子屬性。  
  
## <a name="return-value"></a>傳回值  
 已傳遞至函式物件。  
  
## <a name="remarks"></a>備註  
 `descriptors`引數是包含一或多個描述元物件的物件。  
  
 A*資料屬性*是可以儲存和擷取值的屬性。 包含資料的屬性描述元`value`屬性`writable`屬性，或兩者。 如需詳細資訊，請參閱[資料屬性與存取子屬性](../../javascript/advanced/data-properties-and-accessor-properties.md)。  
  
 *存取子屬性*呼叫使用者提供函式，每次設定或擷取屬性值。 存取子屬性描述元包含`set`屬性`get`屬性，或兩者。  
  
 如果物件已有具有指定的名稱的屬性，會修改該屬性的屬性。 如需詳細資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
 若要建立的物件，並將屬性加入至新的物件，您可以使用[Object.create 函式](../../javascript/reference/object-create-function-javascript.md)。  
  
## <a name="adding-properties"></a>加入屬性  
 在下列範例中，`Object.defineProperties`函式會將資料屬性與存取子屬性加入至使用者定義的物件。  
  
 這個範例會使用物件常值建立`descriptors`物件`newDataProperty`和`newAccessorProperty`描述元物件。  
  
```JavaScript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 就像先前範例中，下列範例會將以動態方式而不是使用物件常值的屬性。  
  
```JavaScript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## <a name="modifying-properties"></a>修改屬性  
 若要修改的物件屬性的屬性，加入下列程式碼。 `Object.defineProperties`函式會修改`writable`屬性`newDataProperty`，並修改`enumerable`屬性`newAccessorProperty`。 它會新增`anotherDataProperty`物件因為該屬性名稱已經存在。  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>需求  
 支援 Internet Explorer 9 標準、 Internet Explorer 10 標準和[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式。 支援 Internet Explorer 8 DOM 物件，否則不支援。  
  
## <a name="see-also"></a>另請參閱  
 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create 函式](../../javascript/reference/object-create-function-javascript.md)   
 [Object 物件](../../javascript/reference/object-object-javascript.md)