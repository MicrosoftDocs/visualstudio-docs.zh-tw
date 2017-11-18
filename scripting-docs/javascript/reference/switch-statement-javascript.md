---
title: "switch 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="switch-statement-javascript"></a>switch 陳述式 (JavaScript)
當指定的運算式值符合標籤時，可讓一或多個陳述式執行。  
  
## <a name="syntax"></a>語法  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>參數  
 `expression`  
 要評估的運算式。  
  
 `label`  
 若要比對識別項`expression`。 如果`label`是`expression`，以開始執行`statementlist`後面的冒號，並繼續進行，直到它遇到任何`break`陳述式，這是選擇性的或結束`switch`陳述式。  
  
 `statementlist`  
 要執行的一個或多個陳述式。  
  
## <a name="remarks"></a>備註  
 使用`default`子句，以提供無標籤的值相符時執行的陳述式`expression`。 它可以在任何位置出現`switch`程式碼區塊。  
  
 零或多個`label`可能指定的區塊。 如果沒有`label`符合值的`expression`，和`default`案例未提供，會執行任何陳述式。  
  
 執行流經`switch`陳述式，如下所示：  
  
-   評估`expression`並查看`label`順序，直到找到相符項目。  
  
-   如果`label`值等於`expression`，執行伴隨`statementlist`。  
  
     繼續執行，直到`break`遇到陳述式，或`switch`陳述式結束。 這表示多個`label`區塊時，會執行`break`陳述式不是。  
  
-   如果沒有`label`等於`expression`，請移至`default`案例。 如果沒有任何`default`情況下，請移至最後一個步驟。  
  
-   在結尾的陳述式繼續執行`switch`程式碼區塊。  
  
## <a name="example"></a>範例  
 下列範例會測試其類型的物件。  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>範例  
 下列程式碼的顯示如果您未使用，會發生什麼事`break`陳述式。  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [if...else 陳述式](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)