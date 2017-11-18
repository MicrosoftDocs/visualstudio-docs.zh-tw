---
title: "length 屬性 (arguments) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>length 屬性 (arguments) (JavaScript)
傳回引數由呼叫端傳遞至函式的實際數目。  
  
## <a name="syntax"></a>語法  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>備註  
 選擇性*函式*引數是目前執行中的名稱`Function`物件。  
  
 **長度**屬性**引數**物件初始化實際數目的引數傳遞至指令碼引擎`Function`物件時在該函式開始執行。  
  
## <a name="example"></a>範例  
 下列範例說明使用**長度**屬性**引數**物件。 若要完全了解的範例，傳遞多個引數必須是 2 個引數比函式：  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用對象**:[引數物件](../../javascript/reference/arguments-object-javascript.md)&#124;[函式物件](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [arguments 屬性 （函式）](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 屬性 （陣列）](../../javascript/reference/length-property-array-javascript.md)   
 [length 屬性 (字串)](../../javascript/reference/length-property-string-javascript.md)