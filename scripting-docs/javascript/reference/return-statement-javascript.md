---
title: "return 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="return-statement-javascript"></a>return 陳述式 (JavaScript)
結束目前的函式，並從該函式傳回值。  
  
## <a name="syntax"></a>語法  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>備註  
 選擇性*運算式*引數是要從函式傳回值。 如果省略，則函式沒有傳回值。  
  
 您使用`return`陳述式來停止執行的函式，並傳回值的*運算式*。 如果*運算式*省略，或沒有`return`從函式中執行陳述式，呼叫目前函式的運算式所指派未定義的值。  
  
## <a name="example"></a>範例  
 以下範例將示範如何使用 `return` 陳述式。  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>範例  
 下列範例說明使用`return`傳回函式的陳述式。  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)