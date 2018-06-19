---
title: delete 方法 (WeakMap) (JavaScript) |Microsoft 文件
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4cec06b77b7198e23d7e455849b5c0bf6d7ff9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636328"
---
# <a name="delete-method-weakmap-javascript"></a>delete 方法 (WeakMap) (JavaScript)
將指定的項目從 `WeakMap` 物件中移除。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
weakmapObj.delete(key)  
```  
  
#### <a name="parameters"></a>參數  
 `weakmapObj`  
 必要項。 `WeakMap` 物件。  
  
 `key`  
 必要項。 要移除的項目索引鍵。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 如果已移除項目，則為 `true`。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入成員`WeakMap`，然後再刪除它。  
  
```JavaScript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]