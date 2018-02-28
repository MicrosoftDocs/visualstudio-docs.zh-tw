---
title: "Object.getOwnPropertyDescriptor 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Object.getOwnPropertyDescriptor 函式 (JavaScript)
取得指定物件特有的屬性描述元。 特有的屬性描述元是直接對物件定義而不是從物件原型繼承而來的描述元。  
  
## <a name="syntax"></a>語法  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>參數  
 `object`  
 必要項。 包含屬性的物件。  
  
 `propertyname`  
 必要項。 屬性的名稱。  
  
## <a name="return-value"></a>傳回值  
 屬性的描述元。  
  
## <a name="remarks"></a>備註  
 您可以使用 `Object.getOwnPropertyDescriptor` 函式取得描述該屬性 (property) 之屬性 (attribute) 的描述元物件。  
  
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)用來加入或修改屬性。  
  
## <a name="data-property-example"></a>資料屬性範例  
 下列範例會取得資料的屬性描述元，並使用該描述元將屬性設為唯讀。  
  
```JavaScript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 如果要列出該屬性的屬性，可以將下列程式碼加入此範例。  
  
```JavaScript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 支援所有的功能。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] 支援 DOM 物件，但不支援使用者定義的物件。 `enumerable` 和 `configurable` 屬性都可以指定，但是不會使用。  
  
## <a name="see-also"></a>另請參閱  
 [文件物件模型原型，第 2 部分： 支援存取子 (getter/setter)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)