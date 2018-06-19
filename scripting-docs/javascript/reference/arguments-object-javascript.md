---
title: arguments 物件 (JavaScript) |Microsoft 文件
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634218"
---
# <a name="arguments-object-javascript"></a>arguments 物件 (JavaScript)
代表目前執行函式之引數的物件，以及呼叫它的函式。  
  
## <a name="syntax"></a>語法  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>參數  
 *function*  
 選擇項。 目前執行中的名稱`Function`物件。  
  
 *n*  
 必要項。 以零為起始的索引引數值傳遞給`Function`物件。  
  
## <a name="remarks"></a>備註  
 您無法明確建立**引數**物件。 **引數**物件時，才可以使用函式就會開始執行。 **引數**函式的物件不是陣列、 但陣列項目進行存取的相同方式存取個別的引數。 索引 *n* 是實際的其中一個參考**0**  ***n*** 屬性**引數**物件。  
  
## <a name="example"></a>範例  
 下列範例說明使用**引數**物件。  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [0...n 屬性 （引數）](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee 屬性 （引數）](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length 屬性 (arguments)](../../javascript/reference/length-property-arguments-javascript.md)