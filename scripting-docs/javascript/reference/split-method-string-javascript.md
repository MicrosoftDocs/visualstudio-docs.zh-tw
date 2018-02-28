---
title: "split 方法 （字串） (JavaScript) |Microsoft 文件"
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
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>split 方法 (字串) (JavaScript)
使用指定的分隔符號將字串分割成子字串，並以陣列方式傳回子字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 要分割的 `String` 物件或字串常值。 此物件不會修改**分割**方法。  
  
 `separator`  
 選擇項。 字串或**規則運算式**物件，可識別用來分隔字串的字元。 如果省略，則會傳回包含整個字串的單一元素陣列。  
  
 `limit`  
 選擇項。 用來限制陣列中所傳回元素個數的值。  
  
## <a name="return-value"></a>傳回值  
 結果**分割**方法是在每個點分隔的字串陣列，其中`separator`常見於`stringObj`。 `separator` 並不會包含在傳回的任何陣列元素中。  
  
## <a name="example"></a>範例  
 下列範例說明使用**分割**方法。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [concat 方法 （字串）](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [捲動、 移動和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)