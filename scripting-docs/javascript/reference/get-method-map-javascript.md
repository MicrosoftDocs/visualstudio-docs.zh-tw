---
title: "get 方法 (Map) (JavaScript) |Microsoft 文件"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-map-javascript"></a>get 方法 (Map) (JavaScript)
傳回對應指定的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>參數  
 `mapObj`  
 必要項。 `Map` 物件。  
  
 `key`  
 必要項。 中的項目索引鍵`Map`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 傳回索引鍵相關聯的物件。 如果`Map`不包含索引鍵，這個方法會傳回`undefined`值。  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取項目從`Map`物件。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]