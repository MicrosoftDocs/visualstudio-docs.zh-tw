---
title: "break 陳述式 (JavaScript) |Microsoft 文件"
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
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>break 陳述式 (JavaScript)
結束目前迴圈或如果搭配`label`，終止相關的陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>備註  
 選擇性`label`引數會指定要中斷的陳述式的標籤。  
  
 您通常會使用`break`陳述式中的`switch`陳述式和`while`， `for`， `for...in`，或`do...while`迴圈。 您最常使用`label`引數中的`switch`陳述式，但是它可以用於任何陳述式，不論是簡單或複合。  
  
 執行`break`陳述式結束目前迴圈或陳述式，並執行指令碼開頭的陳述式後置。  
  
## <a name="examples"></a>範例  
 在此範例中，計數器是設定來計算從 1 到 99 之間。不過，`break`陳述式會在迴圈終止後 14 的計數。  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 下列程式碼，`break`陳述式是指`for`迴圈前面加上`Inner:`陳述式。 當`j`等於 24，`break`陳述式會導致程式流程結束迴圈。 21 到 23 的數字會列印在每一行。  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in..陳述式中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled 陳述式](../../javascript/reference/labeled-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)