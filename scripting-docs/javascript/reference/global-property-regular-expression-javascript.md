---
title: global 屬性 （規則運算式） 的 (JavaScript) |Microsoft 文件
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
- Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637428"
---
# <a name="global-property-regular-expression-javascript"></a>global 屬性 (規則運算式) (JavaScript)
傳回布林值，指出全域旗標的狀態 (**g**) 搭配規則運算式。 預設值是**false**。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>備註  
 所需`rgExp`參考是的執行個體**規則運算式**物件。  
  
 `global`屬性會傳回**true**如果全域旗標設定的規則運算式，並傳回**false**如果不是。  
  
 全域旗標，使用時，表示搜尋應該會發現內搜尋的字串，而不只是第一個模式的所有項目。 這也稱為是全域比對。  
  
## <a name="example"></a>範例  
 下列範例說明使用`global`屬性。 如果您要傳入**g**在函式，如下所示字的所有執行個體"the"會取代單字"a"。 請注意，"The"開頭的字串不會被取代因為**我**（忽略大小寫） 旗標不會傳遞至函式。  
  
 此函式會顯示與允許的規則運算式旗標，也就是相關聯的屬性條件**g**，**我**，和**m**。 此函式也會顯示所做的全部取代字串。  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>範例  
 以下是產生的輸出。  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [ignoreCase 屬性 （規則運算式）](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline 屬性 （規則運算式）](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)