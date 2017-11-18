---
title: "rightContext 屬性 ($&#39;)(RegExp)(JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: rightContext property ($')
ms.assetid: 6999c056-d18c-4583-9dd9-8fbb6d3d0ee7
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d47ea5dd67de9d73ab59b615c567ad3a7a96fb7b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="rightcontext-property-39-regexp-javascript"></a>rightContext 屬性 ($&#39;)(RegExp)(JavaScript)
傳回的字元位置上一次符合搜尋字串的結尾。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
RegExp.rightContext  
```  
  
## <a name="remarks"></a>備註  
 這個屬性與關聯的物件永遠是全域`RegExp`物件。  
  
 初始值**rightContext**屬性為空字串。 值**rightContext**屬性變更時比對成功。  
  
## <a name="example"></a>範例  
 下列範例說明使用**rightContext**屬性：  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**: [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [$1...$9 屬性 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [索引屬性 (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input 屬性 ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex 屬性 (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch 屬性 ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [lastParen 屬性 （$ +） (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [leftContext 屬性 ($`) (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)