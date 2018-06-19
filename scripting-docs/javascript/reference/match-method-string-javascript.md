---
title: match 方法 （字串） (JavaScript) |Microsoft 文件
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
- match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639368"
---
# <a name="match-method-string-javascript"></a>match 方法 (字串) (JavaScript)
比對規則運算式的字串，並傳回陣列，其中包含該搜尋的結果。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 `String`物件或字串常值在其上執行搜尋。  
  
 `rgExp`  
 必要項。 規則運算式物件，其中包含規則運算式模式和適用旗標。 這也可以是變數名稱或字串常值包含規則運算式模式和旗標。  
  
## <a name="remarks"></a>備註  
 如果`match`方法找不到相符項目，它會傳回`null`。 如果找到相符項目，`match`的全域屬性和陣列，會傳回`RegExp`物件會更新以反映比對的結果。  
  
 如果全域旗標 (`g`) 未設定，則為零的陣列會包含整個相符項目，而透過元素 1 的項目 *n* 包含任何子相符項目。 此行為是相同的行為[exec 方法 （規則運算式）](../../javascript/reference/exec-method-regular-expression-javascript.md)時未設定全域旗標。 如果全域旗標設定，透過的項目 0  *n* 包含所發生的所有相符項目。  
  
 如果全域旗標未設定，所傳回的陣列`match`方法有兩個屬性：`input`和`index`。 `input`屬性包含整個搜尋的字串。 `index`屬性包含在完整的搜尋字串中相符的子字串的位置。  
  
 如果旗標`i`已經設定，搜尋不區分大小寫。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `match` 方法。  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [exec 方法 （規則運算式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace 方法 （字串）](../../javascript/reference/replace-method-string-javascript.md)   
 [search 方法 （字串）](../../javascript/reference/search-method-string-javascript.md)   
 [測試方法 （規則運算式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [規則運算式程式設計 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [替代和子運算式 (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [反向參考 (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)