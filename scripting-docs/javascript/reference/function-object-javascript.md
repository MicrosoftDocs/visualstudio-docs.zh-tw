---
title: "函式物件 (JavaScript) |Microsoft 文件"
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Function 物件 (JavaScript)
建立新的函式。  
  
## <a name="syntax"></a>語法  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>語法  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>參數  
 `functionName`  
 必要項。 新建立的函式名稱  
  
 `argname1...argnameN`  
 選擇項。 函數可接受的引數清單。  
  
 `body`  
 選擇項。 字串，包含區塊的[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]函式呼叫時執行程式碼。  
  
## <a name="remarks"></a>備註  
 函式是中的基本資料型別[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。 語法 1 會建立函式值[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]將轉換成`Function`物件時所需。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]將轉換`Function`所建立的物件語法 2 成函式的值時呼叫此函式。  
  
 語法 1 是建立新的函式中的標準方式[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。 語法 2 是用來明確地建立函式物件的替代形式。  
  
 例如，宣告函式可將兩個引數傳遞給它，您可以執行下列其中一種方式：  
  
## <a name="example-1"></a>範例 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>範例 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 在任一情況下，您呼叫函式的一行程式碼如下所示：  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  當您呼叫的函式時，請確定您已包含在括號和任何必要的引數。 呼叫沒有括號內的函式會導致函式本身傳回，而不是函式的傳回值。  
  
## <a name="properties"></a>屬性  
 [0...n 屬性](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)&#124;[arguments 屬性](../../javascript/reference/arguments-property-function-javascript.md)&#124;[callee 屬性](../../javascript/reference/callee-property-arguments-javascript.md)&#124;[caller 屬性](../../javascript/reference/caller-property-function-javascript.md)&#124;[建構函式屬性](../../javascript/reference/constructor-property-object-javascript.md)&#124;[length 屬性 （函式）](../../javascript/reference/length-property-function-javascript.md) &#124;[prototype 屬性](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>方法  
 [apply 方法](../../javascript/reference/apply-method-function-javascript.md)&#124;[方法繫結至](../../javascript/reference/bind-method-function-javascript.md)&#124;[呼叫方法](../../javascript/reference/call-method-function-javascript.md)&#124;[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)&#124;[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)   
 [ew 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var 陳述式](../../javascript/reference/var-statement-javascript.md)