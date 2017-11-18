---
title: "lastIndex 屬性 (RegExp) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex 屬性 (RegExp) (JavaScript)
傳回下一個相符的開始處的字元位置中搜尋的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>備註  
 這個屬性與關聯的物件永遠是全域`RegExp`物件。  
  
 `lastIndex`屬性是以零為起始，亦即，索引的第一個字元為零。 其初始值為-1。 比對成功時，會修改它的值。  
  
 `lastIndex`屬性來修改`exec`和**測試**方法`RegExp`物件，而`match`，**取代**，和**分割**方法`String`物件。  
  
 下列規則適用於值`lastIndex`:  
  
-   如果沒有相符項目，`lastIndex`設定為-1。  
  
-   如果`lastIndex`大於字串的長度**測試**和`exec`失敗和`lastIndex`設定為-1。  
  
-   如果`lastIndex`等於符合規則運算式模式會比對空字串，如果字串的長度。 否則，會比對失敗和`lastIndex`重設為-1。  
  
-   否則，`lastIndex`設定遵循最新的比對的下一個位置。  
  
## <a name="example"></a>範例  
 下列範例說明使用`lastIndex`屬性。 此函式逐一查看搜尋字串，並列印**索引**和`lastIndex`字串中的每個字的值。  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**: [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)