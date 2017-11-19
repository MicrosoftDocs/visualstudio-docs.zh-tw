---
title: "constructor 屬性 (Object) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-object-javascript"></a>constructor 屬性 (Object) (JavaScript)
指定用來建立物件的函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>備註  
 所需`object`是物件或函式的名稱。  
  
 `constructor` 屬性是具有原型之每個物件的原型成員。 這包括所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件除了`Global`和`Math`物件。 `constructor` 屬性包含用來建構該特定物件執行個體的函式參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)