---
title: "測試方法 （規則運算式） 的 (JavaScript) |Microsoft 文件"
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
- test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="test-method-regular-expression-javascript"></a>test 方法 (規則運算式) (JavaScript)
傳回布林值，指出模式存在於中搜尋的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>參數  
 `rgExp`  
 必要項。 執行個體**規則運算式**物件，其中包含規則運算式模式和適用旗標。  
  
 `str`  
 必要項。 執行搜尋的字串。  
  
## <a name="remarks"></a>備註  
 **測試**方法會檢查模式是否存在於字串內，並傳回**true**若是如此，和**false**否則。  
  
 全域屬性`RegExp`物件不會修改**測試**方法。  
  
## <a name="example"></a>範例  
 下列範例說明使用**測試**方法。 若要使用此範例中，將函式傳遞規則運算式模式和字串。 函式會測試規則運算式模式字串中的相符項目，並傳回字串，表示該搜尋的結果：  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)