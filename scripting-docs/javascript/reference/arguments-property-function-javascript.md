---
title: arguments 屬性 （函式） (JavaScript) |Microsoft 文件
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
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633398"
---
# <a name="arguments-property-function-javascript"></a>arguments 屬性 (函式) (JavaScript)
取得目前執行的引數`Function`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>備註  
 `function`引數是目前正在執行的函式的名稱，而且可以省略。  
  
 這個屬性允許來處理引數數目可變的函式。 **長度**屬性`arguments`物件包含傳遞至函數的引數數目。 個別引數中包含`arguments`物件可以存取陣列項目進行存取的方式相同。  
  
## <a name="example"></a>範例  
 下面範例會說明 `arguments` 屬性的使用：  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [arguments 物件](../../javascript/reference/arguments-object-javascript.md)   
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)