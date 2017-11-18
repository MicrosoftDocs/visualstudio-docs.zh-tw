---
title: "$1...$9 屬性 (RegExp) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $1...$9
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: $1...$9 properties
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1926d6281c9003c432c9c9e89a73a48a584ef4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="19-properties-regexp-javascript"></a>$1...$9 屬性 (RegExp) (JavaScript)
傳回所九個最近記憶模式比對期間發現的部分。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
RegExp.$n   
```  
  
## <a name="parameters"></a>參數  
 `RegExp`  
 一律將全域`RegExp`物件。  
  
 `n`  
 從 1 到 9 的任何整數。  
  
## <a name="remarks"></a>備註  
 值**$1...$9**成功括以括號比對時，會修改的屬性。 在規則運算式模式中，可指定任意數目的括號括住的子字串，但會儲存只有最近的九個。  
  
## <a name="example"></a>範例  
 下列範例會執行規則運算式搜尋。 它會顯示相符項目，並從全域 submatches`RegExp`物件。 子相符項目是成功的括號括住相符項目中所包含的`$1...$9`屬性。 此範例也會顯示相符項目，並且 submatches 從傳回的陣列`exec`方法。  
  
```JavaScript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)