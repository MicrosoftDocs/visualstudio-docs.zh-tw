---
title: "呼叫方法 （函式） (JavaScript) |Microsoft 文件"
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
- call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="call-method-function-javascript"></a>call 方法 (函式) (JavaScript)
呼叫物件的方法，以取代目前物件的另一個物件。  
  
## <a name="syntax"></a>語法  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>參數  
 `thisObj`  
 選擇項。 要做為目前物件的物件。  
  
 `arg1, arg2, , argN`  
 選擇項。 要傳遞給方法的引數清單。  
  
## <a name="remarks"></a>備註  
 `call`方法用來代表另一個物件呼叫方法。 它可讓您變更`this`函式從原始內容所指定的新物件的物件`thisObj`。  
  
 如果`thisObj`未提供`global`物件作為`thisObj`。  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用 `call` 方法。  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [函式物件](../../javascript/reference/function-object-javascript.md)   
 [apply 方法 (Function)](../../javascript/reference/apply-method-function-javascript.md)