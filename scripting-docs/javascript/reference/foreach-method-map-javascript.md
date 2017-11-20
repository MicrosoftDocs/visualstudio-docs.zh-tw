---
title: "forEach 方法 (Map) (JavaScript) |Microsoft 文件"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d0ffa12b9a1995df14f4868872238cdc45b674a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-map-javascript"></a>forEach 方法 (Map) (JavaScript)
執行每個項目在對應中指定的動作。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>參數  
 `mapObj`  
 必要項。 `Map` 物件。  
  
 `callbackfn`  
 必要項。 此函式，`forEach`對應中每個項目會呼叫一次。 `callbackfn`接受最多三個引數。 `forEach`呼叫`callbackfn`函式的對應中每個項目一次。  
  
 `thisArg`  
 選擇項。 物件，`this`關鍵字可參考在`callbackfn`函式。 如果省略 `thisArg`，則 `undefined` 就會做為 `this` 值使用。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## <a name="remarks"></a>備註  
 回呼函式的語法如下：  
  
 `function callbackfn(value, key, mapObj)`  
  
 下表所示，您可以使用最多三個參數，宣告回呼函式。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`value`|在對應中所含的值。|  
|`key`|包含對應中索引鍵。|  
|`mapObj`|`Map`周遊的物件。|  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取的成員`Map`使用`forEach`。  
  
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