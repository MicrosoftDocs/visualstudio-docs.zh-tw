---
title: "陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>for 陳述式 (JavaScript)
指定的條件為 true 時，請執行陳述式的區塊。  
  
## <a name="syntax"></a>語法  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>參數  
 `initialization`  
 選擇項。 一個運算式。 這個運算式是只執行一次，才能執行迴圈。  
  
 `test`  
 選擇項。 Boolean 運算式。 如果`test`是`true`，`statement`執行。 如果`test`如果`false`，迴圈會終止。  
  
 `increment`  
 選擇項。 一個運算式。 遞增運算式是在每個迴圈行程結尾執行。  
  
 `statement`  
 選擇項。 如果要執行的一或多個陳述式`test`是**true**。 可以是複合陳述式。  
  
## <a name="remarks"></a>備註  
 您通常使用`for`迴圈迴圈時要執行已知的次數。 A`for`迴圈是可用來逐一查看陣列和執行循序處理。  
  
 條件運算式的測試執行前發生的迴圈，因此`for`陳述式會執行零次以上。  
  
 在任何一行`for`迴圈陳述式區塊中，您可以使用`break`陳述式來結束迴圈，或者您可以使用`continue`陳述式將控制權轉移到迴圈的下一個反覆項目。  
  
## <a name="example"></a>範例  
 在下列範例中，`for`陳述式會執行括住的陳述式，如下所示：  
  
-   首先，變數的初始值`i`評估。  
  
-   然後，只要值`i`小於或等於 9、`document.write`陳述式執行和`i`重新評估。  
  
-   當`i`大於 9、 條件變成 false，控制權會轉移到迴圈外。  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>範例  
 所有的運算式中的`for`陳述式是選擇性的。 在下列範例中，`for`陳述式會建立無限迴圈，而`break`陳述式用來結束迴圈。  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [for...in..陳述式中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)