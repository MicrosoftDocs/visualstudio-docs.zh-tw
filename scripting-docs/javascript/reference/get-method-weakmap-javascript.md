---
title: get 方法 (WeakMap) (JavaScript) |Microsoft 文件
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636488"
---
# <a name="get-method-weakmap-javascript"></a>get 方法 (WeakMap) (JavaScript)
傳回指定的項目從`WeakMap`物件。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>參數  
 `weakmapObj`  
 必要項。 `WeakMap` 物件。  
  
 `key`  
 必要項。 中的項目索引鍵`WeakMap`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 傳回索引鍵相關聯的物件。 如果`WeakMap`不包含索引鍵，這個方法會傳回`undefined`值。  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取成員從`WeakMap`物件。  
  
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