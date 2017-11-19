---
title: "ignoreCase 屬性 （規則運算式） 的 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase 屬性 (規則運算式) (JavaScript)
傳回布林值，指出 ignoreCase 旗標的狀態 (**我**) 搭配規則運算式。 預設值是**false**。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>備註  
 所需`rgExp`參考是的執行個體`RegExp`物件。  
  
 **IgnoreCase**屬性會傳回**true**如果 ignoreCase 旗標設定的規則運算式，並傳回**false**如果不是。  
  
 IgnoreCase 旗標，使用時，表示搜尋在搜尋的字串內的模式比對時，應該忽略區分大小寫。  
  
## <a name="example"></a>範例  
 下列範例說明使用**ignoreCase**屬性。 如果您要傳入"gi"函式，如下所示，這個字的所有執行個體"the"會取代單字"a"，包括初始"The"。 這是因為設定 ignoreCase 旗標，搜尋會忽略任何區分大小寫。 "T"是"t"與相同目的比對。  
  
 此函數會傳回布林值，指出允許的規則運算式旗標，它們的狀態**g**，**我**，和**m**。 函式也會傳回所做的全部取代字串。  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>範例  
 以下是產生的輸出。  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [global 屬性 （規則運算式）](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline 屬性 （規則運算式）](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)