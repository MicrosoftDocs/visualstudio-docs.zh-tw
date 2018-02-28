---
title: "const 陳述式 (JavaScript) |Microsoft 文件"
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>const 陳述式 (JavaScript)
以常數值宣告區塊範圍變數。  
  
## <a name="syntax"></a>語法  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>參數  
 `constant1`  
 所宣告的變數名稱。  
  
 `value1`  
 指派給變數的初始值。  
  
## <a name="remarks"></a>備註  
 使用`const`陳述式來使用的範圍僅限於該區塊的常數值的變數宣告中宣告它。 無法變更變數的值。  
  
 使用宣告的變數`const`必須在宣告時初始化。  
  
## <a name="example"></a>範例  
 以下範例將示範如何使用 `const` 陳述式。  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [let 陳述式](../../javascript/reference/let-statement-javascript.md)   
 [ew 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [變數](../../javascript/variables-javascript.md)