---
title: "索引屬性 (RegExp) (JavaScript) |Microsoft 文件"
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
- index
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Index property
- matching strings
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c6b11a5caf6e727b4d525b9a2d51eddd4542bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="index-property-regexp-javascript"></a>index 屬性 (RegExp) (JavaScript)
搜尋字串中傳回第一個成功的比對的開始處的字元位置。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
RegExp.index   
```  
  
## <a name="remarks"></a>備註  
 這個屬性與關聯的物件永遠是全域`RegExp`物件。  
  
 **索引**屬性是以零為起始。 初始值**索引**屬性為-1。 比對成功時，就會變更其值。  
  
## <a name="example"></a>範例  
 下列範例說明使用**索引**屬性。 此函式逐一查看搜尋字串，並列印**索引**和`lastIndex`字串中的每個字的值。  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**: [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)