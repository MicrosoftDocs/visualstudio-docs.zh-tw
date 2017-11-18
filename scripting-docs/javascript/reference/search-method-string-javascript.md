---
title: "search 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>search 方法 (字串) (JavaScript)
尋找第一個子字串符合規則運算式搜尋中。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 `String`物件或字串常值在其上執行搜尋。  
  
 `rgExp`  
 必要項。 執行個體**規則運算式**物件，其中包含規則運算式模式和適用旗標。  
  
## <a name="return-value"></a>傳回值  
 如果找到相符項目，**搜尋**方法會傳回整數值，指出從字串開頭的位移發生第一個相符項目。 如果找到相符項目，則會傳回-1。  
  
## <a name="remarks"></a>備註  
 您也可以設定`i`旗標，導致不區分大小寫搜尋。  
  
## <a name="example"></a>範例  
 下列範例說明使用**搜尋**方法。  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [exec 方法 （規則運算式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match 方法 （字串）](../../javascript/reference/match-method-string-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace 方法 （字串）](../../javascript/reference/replace-method-string-javascript.md)   
 [測試方法 （規則運算式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [規則運算式程式設計 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)