---
title: "RegExp 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="regexp-object-javascript"></a>RegExp 物件 (JavaScript)
儲存結果的規則運算式模式的相關資訊的內建全域物件比對。  
  
## <a name="syntax"></a>語法  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>備註  
 所需*屬性*引數可以是任何一個`RegExp`物件屬性。  
  
 `RegExp`物件無法直接建立，而是一律可供使用。 成功的規則運算式搜尋完成後之前, 的各種屬性的初始值`RegExp`物件如下：  
  
|屬性|縮寫|初始值|  
|--------------|---------------|-------------------|  
|索引||-1|  
|輸入|$_|空字串。|  
|lastIndex||-1|  
|lastMatch|$&|空字串。|  
|lastParen|$+|空字串。|  
|leftContext|$`|空字串。|  
|rightContext|$'|空字串。|  
|$1 - $9|$1 - $9|空字串。|  
  
 成功的規則運算式搜尋完成後，才會為它們的值擁有未定義其屬性。  
  
 全域`RegExp`物件不應該與混淆**規則運算式**物件。 即使它們看起來像是相同的作業，它們是不同的。 全域屬性`RegExp`物件包含的每個相符項目的持續更新的資訊，因為它發生時的屬性**規則運算式**物件包含的資訊就會發生的符合項目與該執行個體的**規則運算式**。  
  
## <a name="example"></a>範例  
 下列範例會執行規則運算式搜尋。 它會顯示相符項目，並從全域 submatches`RegExp`物件，並從所傳回的陣列`exec`方法。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>屬性  
 [$1...$9 屬性](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)&#124;[索引屬性](../../javascript/reference/index-property-regexp-javascript.md)&#124;[input 屬性](../../javascript/reference/input-property-dollar-regexp-javascript.md)&#124;[lastIndex 屬性](../../javascript/reference/lastindex-property-regexp-javascript.md)&#124;[lastMatch 屬性](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)&#124;[lastParen 屬性](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)&#124;[leftContext 屬性](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)&#124;[rightContext 屬性](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>方法  
 `RegExp`物件有沒有任何方法。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 物件](../../javascript/reference/string-object-javascript.md)