---
title: "length 屬性 （函式） (JavaScript) |Microsoft 文件"
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
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-function-javascript"></a>length 屬性 (函式) (JavaScript)
取得定義的函式的引數數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>備註  
 所需*functionName*函式的名稱。  
  
 **長度**函式的執行個體建立時，函式的屬性會初始化指令碼引擎中的函式定義的引數的數字。  
  
 引數的值不同數目的呼叫函式時，會發生什麼事其**長度**屬性函式而定。  
  
## <a name="example"></a>範例  
 下列範例說明使用**長度**屬性：  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [arguments 屬性 （函式）](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 屬性 （陣列）](../../javascript/reference/length-property-array-javascript.md)   
 [length 屬性 (字串)](../../javascript/reference/length-property-string-javascript.md)