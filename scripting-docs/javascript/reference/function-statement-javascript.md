---
title: 函式陳述式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636868"
---
# <a name="function-statement-javascript"></a>function 陳述式 (JavaScript)
宣告新的函式。  
  
## <a name="syntax"></a>語法  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>參數  
 `functionname`  
 必要項。 函式的名稱。  
  
 `arg1...argN`  
 選擇項。 此函式了解的引數之選擇性的逗號分隔清單。  
  
 `statements`  
 選擇項。 一或多個[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]陳述式。  
  
## <a name="remarks"></a>備註  
 使用`function`陳述式來宣告的函式，供日後使用。 中所包含的程式碼`statements`從指令碼中的其他地方呼叫此函數時，才可以執行。  
  
 [傳回](../../javascript/reference/return-statement-javascript.md)陳述式用於從函式傳回值。 您沒有使用`return`陳述式，則程式會傳回到達在函式結束時。 如果沒有`return`執行陳述式在函式，或如果`return`陳述式沒有運算式，此函數會傳回值`undefined`。  
  
> [!NOTE]
>  當您呼叫的函式時，請務必包含括號和任何必要的引數。 呼叫沒有括號內的函式傳回函式，而不函式的結果的參考。  
  
## <a name="example"></a>範例  
 以下範例將示範如何使用 `function` 陳述式。  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>範例  
 函式可以指派給變數。 下列範例可說明此點。  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)