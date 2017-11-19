---
title: "while 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="while-statement-javascript"></a>while 陳述式 (JavaScript)
執行陳述式或系列的陳述式，直到指定的條件是`false`。  
  
## <a name="syntax"></a>語法  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>參數  
 `expression`  
 必要項。 布林運算式檢查迴圈的每個反覆項目之前。 如果`expression`是`true`，迴圈執行。 如果`expression`是`false`，迴圈會終止。  
  
 `statements`  
 選擇項。 如果要執行的一或多個陳述式`expression`是`true`。  
  
## <a name="remarks"></a>備註  
 `while`陳述式檢查`expression`第一次執行迴圈之前。 如果`expression`是`false`在這個階段中，永遠不會執行迴圈。  
  
## <a name="example"></a>範例  
 以下範例將示範如何使用 `while` 陳述式。  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)