---
title: "in 運算子 (JavaScript) |Microsoft 文件"
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="in-operator-javascript"></a>in 運算子 (JavaScript)
測試物件中的屬性是否存在。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>參數  
 `result`  
 必要項。 任何變數。  
  
 `property`  
 必要項。 運算式評估為字串運算式。  
  
 `object`  
 必要項。 任何物件。  
  
## <a name="remarks"></a>備註  
 `in`運算子會判斷物件是否具有內容，名為`property`。 它也會判斷屬性是否為物件的原型鏈結的一部分。 如需物件原型的詳細資訊，請參閱[原型和原型繼承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`in`運算子：  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)