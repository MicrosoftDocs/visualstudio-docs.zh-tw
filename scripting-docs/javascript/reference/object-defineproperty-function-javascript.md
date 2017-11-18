---
title: "Object.defineProperty 函式 (JavaScript) |Microsoft 文件"
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
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty 函式 (JavaScript)
將屬性加入至物件，或修改現有屬性 (Property) 的屬性 (Attribute)。  
  
## <a name="syntax"></a>語法  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>參數  
 `object`  
 必要項。 要加入或修改屬性的目標物件。 這可以是原生 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件 (也就是使用者定義的物件或內建物件) 或 DOM 物件。  
  
 `propertyname`  
 必要項。 包含屬性名稱的字串。  
  
 `descriptor`  
 必要項。 屬性的描述元。 可用於資料屬性或存取子屬性。  
  
## <a name="return-value"></a>傳回值  
 修改過的物件。  
  
## <a name="remarks"></a>備註  
 您可以使用 `Object.defineProperty` 函式執行下列動作：  
  
-   將新的屬性加入物件。 當物件沒有指定的屬性名稱時，就會發生這種情況。  
  
-   修改現有屬性 (Property) 的屬性 (Attribute)。 當物件已經指定屬性名稱時，就會發生這種情況。  
  
 屬性 (Property) 定義會在描述元物件上提供，該物件會描述資料屬性 (Property) 或存取子屬性 (Property) 的屬性 (Attribute)。 描述元物件是 `Object.defineProperty` 函式的參數。  
  
 若要將多個屬性加入物件，或修改現有的多個屬性，您可以使用[Object.defineProperties 函式](../../javascript/reference/object-defineproperties-function-javascript.md)。  
  
## <a name="exceptions"></a>例外狀況  
 如果下列任何一個條件成立，就會擲回 `TypeError` 例外狀況：  
  
-   `object` 引數不是物件。  
  
-   物件不是[可擴充](../../javascript/reference/object-isextensible-function-javascript.md)和指定的屬性名稱不存在...  
  
-   `descriptor` 具有 `value` 或 `writable` 屬性，而且也有 `get` 或 `set` 屬性。  
  
-   `descriptor` 具有並非函式或未定義的 `get` 或 `set` 屬性。  
  
-   指定的屬性 (Property) 名稱已經存在，現有的屬性 (Property) 具有 `false` 的 `configurable` 屬性 (Attribute)，而且 `descriptor` 包含與現有屬性 (Property) 不同的一個或多個屬性 (Attribute)。 不過，當現有的屬性 (Property) 具有 `false` 的 `configurable` 屬性 (Attribute) 及 `true` 的 `writable` 屬性 (Attribute) 時，允許 `value` 或 `writable` 屬性 (Attribute) 不同。  
  
## <a name="adding-a-data-property"></a>加入資料屬性  
 在下列範例中，`Object.defineProperty` 函式會將資料屬性加入使用者定義的物件。 若要改為將屬性加入現有 DOM 物件，請取消 `var = window.document` 程式碼行的註解。  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 若要列出物件屬性，請將下列程式碼加入這個範例。  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>修改資料屬性  
 若要修改物件之屬性 (Property) 的屬性 (Attribute)，請將下列程式碼加入之前顯示的 `addDataProperty` 函式。 `descriptor` 參數只包含一個 `writable` 屬性。 其他資料屬性 (Property) 的屬性 (Attribute) 維持不變。  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>加入存取子屬性  
 在下列範例中，`Object.defineProperty` 函式會將存取子屬性加入使用者定義的物件。  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 若要列出物件屬性，請將下列程式碼加入這個範例。  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>修改存取子屬性  
 若要修改物件之屬性 (Property) 的屬性 (Attribute)，請將下列程式碼加入之前顯示的程式碼。 `descriptor` 參數僅包含 `get` 存取子定義。 其他屬性 (Property) 的屬性 (Attribute) 維持不變。  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>修改 DOM 項目的屬性  
 下列範例示範如何使用 `Object.getOwnPropertyDescriptor` 函式取得和修改屬性的屬性描述元，以自訂內建 DOM 屬性。 在這個範例中，必須有一個 DIV 項目的 ID 為 "div"。  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>需求  
 Internet Explorer 9 標準模式、Internet Explorer 10 標準模式，以及 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式皆支援所有功能。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] 支援 DOM 物件，但不支援使用者定義的物件。 `enumerable` 和 `configurable` 屬性都可以指定，但是不會使用。  
  
## <a name="see-also"></a>另請參閱  
 [文件物件模型原型，第 2 部分： 支援存取子 (getter/setter)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperties 函式](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.create 函式](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)