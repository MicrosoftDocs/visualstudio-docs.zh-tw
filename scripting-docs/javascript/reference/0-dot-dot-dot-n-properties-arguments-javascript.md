---
title: "0...n 屬性 (arguments) (JavaScript) |Microsoft 文件"
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
- 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>0...n 屬性 (引數) (JavaScript)
傳回個別的引數的實際值**引數**所傳回物件**引數**屬性執行的函式。  
  
## <a name="syntax"></a>語法  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>參數  
 *function*  
 選擇項。 目前執行中的名稱`Function`物件。  
  
 0、 1、 2、 *、 n*  
 必要項。 非負整數，範圍內的 0 到 *n* 其中 0 代表第一個引數和 *n* 代表最後一個引數。 最後一個引數的值 *n* 是**arguments.length 1**。  
  
## <a name="remarks"></a>備註  
 傳回 0 的值。 . . n 個屬性是傳遞至執行的函式的實際值。 時，實際上並未引數的陣列，個別引數組成**引數**物件存取陣列項目進行存取的方式相同。  
  
## <a name="example"></a>範例  
 下列範例說明使用**0...**  ***n***屬性的**引數**物件。 若要完全了解的範例，將一個或多個引數至函式：  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用對象**:[引數物件](../../javascript/reference/arguments-object-javascript.md)&#124;[函式物件](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [length 屬性 (arguments)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length 屬性 (函式)](../../javascript/reference/length-property-function-javascript.md)