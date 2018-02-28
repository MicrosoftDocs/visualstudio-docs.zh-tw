---
title: "Map 物件 (JavaScript) |Microsoft 文件"
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
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Map 物件 (JavaScript)
索引鍵/值組的集合。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>備註  
 索引鍵與集合中的值可以是任何型別。 如果您使用現有的索引鍵將某個值加入至集合，則新的值會取代舊的值。  
  
## <a name="properties"></a>屬性  
 下表列出 `Map` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[建構函式](../../javascript/reference/constructor-property-map.md)|指定建立對應的函式。|  
|[原型](../../javascript/reference/prototype-property-map.md)|傳回對應的原型參考。|  
|[size](../../javascript/reference/size-property-map-javascript.md)|傳回對應中的項目數目。|  
  
## <a name="methods"></a>方法  
 下表列出 `Map` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|從對應移除所有項目。|  
|[刪除](../../javascript/reference/delete-method-map-javascript.md)|從對應中移除指定的項目。|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|執行每個項目在對應中指定的動作。|  
|[get](../../javascript/reference/get-method-map-javascript.md)|傳回對應指定的項目。|  
|[具有](../../javascript/reference/has-method-map-javascript.md)|傳回`true`如果對應包含指定的項目。|  
|[set](../../javascript/reference/set-method-map-javascript.md)|將新項目加入至對應。|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|傳回對應的字串表示。|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|傳回指定物件的基本值。|  
  
## <a name="example"></a>範例  
 下面範例會示範如何將成員加入至 `Map`，然後擷取這些成員。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]