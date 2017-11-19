---
title: "do...while 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>do...while 陳述式 (JavaScript)
執行陳述式區塊一次，並接著重複執行迴圈，直到條件運算式會評估為`false`。  
  
## <a name="syntax"></a>語法  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>參數  
 `statement`  
 必要項。 如果要執行的陳述式`expression`是`true`。 可以是複合陳述式。  
  
 `expression`  
 必要項。 可以強制轉型為布林值的運算式`true`或`false`。 如果`expression`是`true`，再次執行迴圈。 如果`expression`是`false`，迴圈會終止。  
  
## <a name="remarks"></a>備註  
 不同於`while`陳述式，`do...while`迴圈執行之前的條件運算式會評估一次。  
  
 在任何一行`do...while`區塊中，您可以使用`break`陳述式讓程式流程結束迴圈，或者您可以使用`continue`陳述式直接前往`while`運算式。  
  
## <a name="example"></a>範例  
 在下列範例中的陳述式`do...while`迴圈會繼續執行長達變數`i`低於 10。  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>範例  
 在下列範例中，在迴圈內的陳述式會執行一次即使不符合的條件。  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in..陳述式中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)   
 [Labeled 陳述式](../../javascript/reference/labeled-statement-javascript.md)