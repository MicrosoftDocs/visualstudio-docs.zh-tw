---
title: continue 陳述式 (JavaScript) |Microsoft 文件
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
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636378"
---
# <a name="continue-statement-javascript"></a>continue 陳述式 (JavaScript)
停止迴圈目前的反覆項目，並啟動新的反覆項目。  
  
## <a name="syntax"></a>語法  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>備註  
 選擇性`label`引數指定的陳述式`continue`套用。  
  
 您可以使用`continue`陳述式僅內部`while`， `do...while`，**如**，或`for...in`迴圈。 執行`continue`陳述式停止迴圈的目前反覆項目，並繼續使用迴圈開頭的程式流程。 這有下列不同類型的迴圈影響：  
  
-   `while`和`do...while`迴圈測試其條件，而如果為 true，執行迴圈一次。  
  
-   `for`迴圈執行它們的遞增運算式，而如果測試運算式為 true，執行迴圈一次。  
  
-   `for...in`迴圈繼續進行下一個欄位指定的變數，並再次執行迴圈。  
  
## <a name="examples"></a>範例  
 在此範例中，迴圈會逐一查看從 1 到 9。 陳述式之間`continue`和結尾`for`主體會略過，因為使用了`continue`陳述式與運算式`(i < 5)`。  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 下列程式碼，`continue`陳述式是指`for`迴圈前面加上`Inner:`標籤。 當`j`為 24，`continue`陳述式會造成的`for`迴圈移至下一個反覆項目。 數字 21 透過 23 和 25 30 到列印在每一行。  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in..陳述式中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled 陳述式](../../javascript/reference/labeled-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)