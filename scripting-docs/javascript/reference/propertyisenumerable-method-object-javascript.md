---
title: "propertyIsEnumerable 方法 (Object) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable 方法 (Object) (JavaScript)
判斷指定的屬性是否為可列舉。  
  
## <a name="syntax"></a>語法  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>參數  
 `object`  
 必要項。 物件的執行個體。  
  
 `proName`  
 必要項。 屬性名稱的字串值。  
  
## <a name="remarks"></a>備註  
 `propertyIsEnumerable`方法會傳回`true`如果`proName`存在於`object`，可以使用列舉`For`迴圈。 `propertyIsEnumerable`方法會傳回`false`如果`object`不具有指定之名稱的屬性或指定的屬性不是可列舉。 一般而言，預先定義的屬性不是可列舉的但使用者定義的屬性都可列舉。  
  
 `propertyIsEnumerable`方法不會考慮的原型鏈結中的物件。  
  
## <a name="example"></a>範例  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)