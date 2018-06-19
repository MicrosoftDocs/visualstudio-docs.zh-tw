---
title: replace 方法 （字串） (JavaScript) |Microsoft 文件
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
- replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82894a5d7f92c8231a6ba3a1948369fb2c819a6d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
ms.locfileid: "27719340"
---
# <a name="replace-method-string-javascript"></a>replace 方法 (String) (JavaScript)
使用規則運算式或搜尋字串取代字串中的文字。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringObj.replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>參數  
 `stringObj`  
 必要。 要執行取代的 `String` 物件或字串常值。 這個字串不會修改**取代**方法。 不過，這個方法的傳回值是由取代所產生的字串。  
  
 `rgExp`  
 必要。 執行個體**規則運算式**物件，其中包含規則運算式模式和適用旗標。 也可以是代表規則運算式的 `String` 物件或字串常值。 如果`rgExp`不是執行個體的**規則運算式**物件，它會轉換為字串，並對結果進行完全相符搜尋; 不嘗試將字串轉換為規則運算式。  
  
 `replaceText`  
 必要。 `String` 物件或字串常值，其中包含每次成功比對 `rgExp` 中的 `stringObj` 時用來取代的文字。 在 [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本中，`replaceText` 引數也可以做為傳回取代文字的函式。  
  
## <a name="return-value"></a>傳回值  
 結果**取代**方法是一份`stringObj`指定之取代動作已完成。  
  
## <a name="remarks"></a>備註  
 下列任何比對變數都可以用來識別最近的相符項目及從中產生的字串。 比對變數可以在文字取代中使用，其中的取代字串必須以動態方式決定。  
  
|字元|意義|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本)|  
|**$&**|指定整個模式比對之 `stringObj` 的部分  ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本)|  
|`$``|指定的該部分`stringObj`之前所描述的相符項目 **$&** 。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本)|  
|`$'`|指定的該部分`stringObj`一節所描述的相符項目 **$&** 。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本)|  
|`$`  ***n***| *n*個擷取的子相符項目，其中 *n* 是從 1 到 9 的單一十進位數字。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本)|  
|`$`  ***nn***| *nn*個擷取的子相符項目，其中 *nn* 是從 01 到 99 的二位數十進位數。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本)|  
  
 如果`replaceText`是函數，針對每個相符的子字串的函式會以下列呼叫*m* + 3 引數其中*m*是左邊擷取括號中的數字`rgExp`。 第一個引數是相符的子字串。 下一步 *m*引數是所有搜尋所產生的擷取。 引數*m* + 2 是中的位移`stringObj`位置比對，而引數*m* + 3 則是`stringObj`。 結果會產生字串值，這是使用對應之函式呼叫的傳回值來取代每一個相符子字串所產生的結果。  
  
 **取代**方法更新的全域屬性`RegExp`物件。  
  
## <a name="example"></a>範例  
 下列範例說明使用**取代**方法，以將所有的"the"取代成"a"  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 此外，**取代**方法也可取代模式中的子運算式。 下列範例會交換字串中的每一對文字。  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumped lazy the dog.  
```  
  
 下列範例適用於 [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] (含) 以後版本，將示範如何使用傳回取代文字的函式。 它會以攝氏度數取代後面接著 "F" 的任何數字。  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>請參閱  
 [exec 方法 （規則運算式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match 方法 （字串）](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [search 方法 （字串）](../../javascript/reference/search-method-string-javascript.md)   
 [測試方法 （規則運算式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [規則運算式程式設計 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [替代和子運算式 (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [反向參考 (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 拖放範例應用程式](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)