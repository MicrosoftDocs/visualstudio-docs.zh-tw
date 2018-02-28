---
title: "WeakMap 物件 (JavaScript) |Microsoft 文件"
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
- WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>WeakMap 物件 (JavaScript)
每個索引鍵都是物件參考之索引鍵/值組的集合。  
  
## <a name="syntax"></a>語法  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>備註  
 A`WeakMap`無法列舉物件。  
  
 如果您使用現有的索引鍵將某個值加入至集合，則新的值會取代舊的值。  
  
 在`WeakMap`物件以保存 '弱' 索引鍵物件的參考。 這表示`WeakMap`不會導致索引鍵的物件發生記憶體回收。 當沒有參考 (以外`WeakMap`) 索引鍵的物件，記憶體回收行程可能會回收索引鍵的物件。  
  
## <a name="properties"></a>屬性  
 下表列出 `WeakMap` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[建構函式](../../javascript/reference/constructor-property-weakmap.md)|指定用來建立 `WeakMap` 的函式。|  
|[原型](../../javascript/reference/prototype-property-weakmap.md)|傳回 `WeakMap` 的原型參考。|  
  
## <a name="methods"></a>方法  
 下表列出 `WeakMap` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|將所有項目從 `WeakMap` 移除。|  
|[刪除](../../javascript/reference/delete-method-weakmap-javascript.md)|移除指定的項目從`WeakMap`。|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|傳回指定的項目從`WeakMap`。|  
|[具有](../../javascript/reference/has-method-weakmap-javascript.md)|傳回`true`如果`WeakMap`包含指定的項目。|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|將新項目加入 `WeakMap`。|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|傳回的字串表示`WeakMap`。|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|傳回指定物件的基本值。|  
  
## <a name="example"></a>範例  
 下列範例示範如何將成員加入`WeakMap`物件，然後再擷取。  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]