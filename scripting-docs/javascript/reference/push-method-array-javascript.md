---
title: "push 方法 （陣列） (JavaScript) |Microsoft 文件"
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
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="push-method-array-javascript"></a>push 方法 (陣列) (JavaScript)
附加新項目到陣列中，並傳回陣列的新長度。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 `Array` 物件。  
  
 `item, item2,. . ., itemN`  
 選擇項。 新的項目`Array`。  
  
## <a name="remarks"></a>備註  
 `push`和`pop`方法可讓您模擬後進先出堆疊。  
  
 `push`方法會附加它們出現的順序中的項目。 如果其中一個引數為陣列時，它會新增為單一項目。 使用`concat`方法以便加入從兩個或多個陣列項目。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `push` 方法。  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [concat 方法 （陣列）](../../javascript/reference/concat-method-array-javascript.md)   
 [pop 方法 (Array)](../../javascript/reference/pop-method-array-javascript.md)