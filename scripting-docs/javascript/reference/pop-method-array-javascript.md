---
title: "pop 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="pop-method-array-javascript"></a>pop 方法 (陣列) (JavaScript)
移除陣列的最後一個項目，然後將它傳回。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>備註  
 [發送](../../javascript/reference/push-method-array-javascript.md)和`pop`方法可讓您模擬堆疊，它會使用最後先進先出 (LIFO) 來儲存資料的原則。  
  
 所需`arrayObj`參考是`Array`物件。  
  
 如果陣列是空的`undefined`傳回。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `pop` 方法。  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [push 方法 (Array)](../../javascript/reference/push-method-array-javascript.md)