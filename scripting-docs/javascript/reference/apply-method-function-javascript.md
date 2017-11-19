---
title: "apply 方法 （函式） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="apply-method-function-javascript"></a>apply 方法 (函式) (JavaScript)
呼叫函式，以指定的物件取代`this`函式和指定之陣列的函式的引數的值。  
  
## <a name="syntax"></a>語法  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>參數  
 `thisObj`  
 選擇項。 要做為物件`this`物件。  
  
 `argArray`  
 選擇項。 一組要傳遞至函數的引數。  
  
## <a name="remarks"></a>備註  
 如果`argArray`不是有效的物件，則會發生 「 物件必須是 「 錯誤。  
  
 如果沒有`argArray`也`thisObj`提供時，原始`this`物件作為`thisObj`沒有引數會傳遞。  
  
## <a name="example"></a>範例  
 下列程式碼會示範如何使用套用的方法。  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)