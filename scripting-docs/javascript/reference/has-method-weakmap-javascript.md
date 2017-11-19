---
title: "has 方法 (WeakMap) (JavaScript) |Microsoft 文件"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakmap-javascript"></a>has 方法 (WeakMap) (JavaScript)
傳回`true`如果`WeakMap`物件包含指定的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>參數  
 `weakmapObj`  
 必要項。 `WeakMap` 物件。  
  
 `key`  
 必要項。 若要測試的項目索引鍵。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `true`如果`WeakMap`包含指定之索引鍵。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入成員`WeakMap`，然後使用`has`來檢查是否存在。  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]