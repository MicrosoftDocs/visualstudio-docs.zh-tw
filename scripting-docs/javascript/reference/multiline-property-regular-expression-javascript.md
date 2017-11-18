---
title: "multiline 屬性 （規則運算式） 的 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline 屬性 (規則運算式) (JavaScript)
傳回布林值，指出多行的旗標的狀態 (**m**) 搭配規則運算式。 預設值是**false**。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>備註  
 所需`rgExp`引數是的執行個體`RegExp`物件  
  
 **多行**屬性會傳回**true**如果多行的旗標設定的規則運算式，並傳回**false**如果不是。 **多行**屬性是**true**如果規則運算式物件是否使用建立**m**旗標。  
  
 如果**多行**是**false**，"^"符合的字串，而"$"相符項目開頭位置的字串結尾的位置。 如果**多行**是**true**，"^"著"\n"或"\r"、"$"的位置比對字串結尾的位置以及先前"\n 的位置比對以及字串的開頭位置"或"\r"。  
  
## <a name="example"></a>範例  
 下列範例說明的行為**多行**屬性。 如果您將"m"中函式，如下所示，"while"這個字會取代單字"和"。 這是因為設定多行的旗標和"while"這個字，就會發生在新行字元後面一行的開頭。 多行的旗標允許在多行字串上執行搜尋。  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [global 屬性 （規則運算式）](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase 屬性 （規則運算式）](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)