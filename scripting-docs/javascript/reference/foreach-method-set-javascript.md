---
title: "forEach 方法 (Set) (JavaScript) |Microsoft 文件"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-set-javascript"></a>forEach 方法 (Set) (JavaScript)
執行每個項目集合中指定的動作。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>參數  
 `setObj`  
 必要項。 `Set` 物件。  
  
 `callbackfn`  
 必要項。 `callbackfn`接受最多三個引數。 此函式，`forEach`集中每個項目會呼叫一次。  
  
 `thisArg`  
 選擇項。 物件，`this`關鍵字可參考在`callbackfn`函式。 如果省略 `thisArg`，則 `undefined` 就會做為 `this` 值使用。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## <a name="remarks"></a>備註  
 回呼函式的語法如下：  
  
 `function callbackfn(value, key, setObj)`  
  
 下表所示，您可以使用最多三個參數，宣告回呼函式。  
  
|回呼引數|定義|  
|-----------------------|----------------|  
|`value`|在集合中包含的值。|  
|`key`|在集合中包含的值。 一組不包含金鑰，因此這個值是相同`value`。|  
|`setObj`|`Set`周遊的物件。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `forEach`。 `callbackfn`引數包含回呼函式的程式碼。  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>範例  
 下列範例顯示，所以您也可以擷取從一組的成員將只有一個參數傳遞至回呼函式。  
  
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