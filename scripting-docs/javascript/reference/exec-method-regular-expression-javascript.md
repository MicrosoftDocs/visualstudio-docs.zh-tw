---
title: exec 方法 （規則運算式） 的 (JavaScript) |Microsoft 文件
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
- exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637038"
---
# <a name="exec-method-regular-expression-javascript"></a>exec 方法 (規則運算式) (JavaScript)
使用規則運算式模式，在字串上執行搜尋並傳回陣列，其中包含該搜尋的結果。  
  
## <a name="syntax"></a>語法  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>參數  
 `rgExp`  
 必要項。 執行個體**規則運算式**物件，其中包含規則運算式模式和適用旗標。  
  
 `str`  
 必要項。 `String`物件或字串常值在其上執行搜尋。  
  
## <a name="remarks"></a>備註  
 如果`exec`方法找不到相符項目，它會傳回`null`。 如果找到相符項目，`exec`的全域屬性和陣列，會傳回`RegExp`物件會更新以反映比對的結果。 陣列的零個項目包含整個相符項目，而元素 1-  *n* 包含相符項目內所發生的任何子相符項目。 此行為是相同的行為`match`方法，而不全域旗標 (**g**) 設定。  
  
 如果規則運算式，設定全域旗標`exec`搜尋字串開頭的值所指示之位置`lastIndex`。 如果未設定全域旗標，`exec`會忽略此值的`lastIndex`和從字串的開頭進行搜尋。  
  
 所傳回的陣列`exec`方法有三個屬性，**輸入**，**索引**和**lastIndex。** **輸入**屬性包含整個搜尋的字串。 **索引**屬性包含在完整的搜尋字串中相符的子字串的位置。 `lastIndex`屬性包含在比對最後一個字元之後的位置。  
  
## <a name="example"></a>範例  
 下列範例說明使用`exec`方法：  
  
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
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [match 方法 （字串）](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search 方法 （字串）](../../javascript/reference/search-method-string-javascript.md)   
 [測試方法 （規則運算式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [規則運算式程式設計 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)