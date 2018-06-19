---
title: __proto__屬性 (Object) (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8659c7a4ece5e30378838f20341ec6712f77ca3
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899571"
---
# <a name="proto-property-object-javascript"></a>__proto__屬性 (Object) (JavaScript)
包含指定之物件的內部原型的參考。  

> [!WARNING]
> `__proto__`屬性是舊版的功能。 使用[Object.getPrototypeOf](../reference/object-getprototypeof-function-javascript.md)改為。
  
## <a name="syntax"></a>語法  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要。 要設定的原型物件。  
  
## <a name="remarks"></a>備註  
 `__proto__`屬性可以用來設定物件的原型。  
  
 物件或函式會繼承所有方法和屬性以及所有方法和屬性的新原型的原型鏈結中的新原型。 物件可以有只有單一的原型 （不包括繼承的原型的原型鏈結中），因此當您呼叫`__proto__`屬性，取代先前的原型。  
  
 您可以只在可延伸的物件上設定原型。 如需詳細資訊，請參閱[Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)。  
  
> [!NOTE]
>  `__proto__`屬性名稱開頭和結尾是兩個底線。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何設定物件的原型。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何透過將屬性新增至原則，以將屬性新增至物件。  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會將屬性新增至 `String` 物件，方法是對此物件設定新原型。  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [原型和原型繼承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)