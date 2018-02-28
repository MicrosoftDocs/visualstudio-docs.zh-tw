---
title: "設定物件 (JavaScript) |Microsoft 文件"
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
- Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Set 物件 (JavaScript)
可屬於任何類型的唯一值集合。  
  
## <a name="syntax"></a>語法  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>備註  
 如果您嘗試加入非唯一值以`Set`，新值將不會加入至集合。  
  
## <a name="properties"></a>屬性  
 下表列出 `Set` 物件的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[建構函式](../../javascript/reference/constructor-property-set.md)|指定用來建立集合的函式。|  
|[原型](../../javascript/reference/prototype-property-set.md)|傳回集合的原型參考。|  
|[size](../../javascript/reference/size-property-set-javascript.md)|傳回集合中的項目數目。|  
  
## <a name="methods"></a>方法  
 下表列出 `Set` 物件的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|將項目加入集合。|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|從集合移除所有項目。|  
|[刪除](../../javascript/reference/delete-method-set-javascript.md)|將指定的項目從集合中移除。|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|執行每個項目集合中指定的動作。|  
|[具有](../../javascript/reference/has-method-set-javascript.md)|如果集合包含指定的項目，則傳回 `true`。|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|傳回一組的字串表示。|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|傳回指定物件的基本值。|  
  
## <a name="example"></a>範例  
 下面範例會示範如何將成員加入至集合 (Set)，然後擷取這些成員。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]