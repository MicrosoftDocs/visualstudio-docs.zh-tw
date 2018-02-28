---
title: "let 陳述式 (JavaScript) |Microsoft 文件"
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
- let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>let 陳述式 (JavaScript)
宣告區塊範圍變數。  
  
## <a name="syntax"></a>語法  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>參數  
 `variable1`  
 所宣告的變數名稱。  
  
 `value1`  
 指派給變數的初始值。  
  
## <a name="remarks"></a>備註  
 使用`let`陳述式來宣告一個變數，其中的範圍僅限於在區塊中宣告它。 當您宣告的變數，或稍後在您的指令碼中，您可以指派值。  
  
 使用宣告的變數`let`不能使用它的宣告或錯誤會造成之前。  
  
 如果您未初始化的變數`let`陳述式，它會自動指派[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]值`undefined`。  
  
## <a name="example"></a>範例  
 以下範例將示範如何使用 `let` 陳述式。  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [const 陳述式](../../javascript/reference/const-statement-javascript.md)   
 [ew 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [變數](../../javascript/variables-javascript.md)