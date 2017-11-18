---
title: "for...in..陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="forin-statement-javascript"></a>for...in 陳述式 (JavaScript)
執行一或多個陳述式的物件，每個屬性或陣列的每個項目。  
  
## <a name="syntax"></a>語法  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>參數  
 `variable`  
 必要項。 可以是任何屬性名稱的變數`object`或的任何項目索引`array`。  
  
 `object`, `array`  
 選擇項。 物件或陣列要反覆查看。  
  
 `statements`  
 選擇項。 要執行的每一個屬性的一或多個陳述式`object`或每個項目`array`。 可以是複合陳述式。  
  
## <a name="remarks"></a>備註  
 在每次反覆運算迴圈時，值的開頭`variable`是下一個屬性名稱的`object`或下一個項目索引的`array`。 然後您可以使用`variable`中任何陳述式參考的屬性在迴圈內部`object`或項目`array`。  
  
 物件的屬性不會指派以確定的方式。 您無法依據索引，指定特定的屬性，只能由屬性的名稱。  
  
 逐一查看陣列元素的順序，也就是 0、 1、 2 中執行。  
  
## <a name="example"></a>範例  
 下列範例說明使用`for...in`陳述式搭配使用以關聯陣列的物件。  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>範例  
 此範例說明如何使用`for ... in`陳述式來逐一查看`Array`具有 expando 屬性的物件。  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  使用`Enumerator`物件來逐一查看集合的成員。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../../javascript/reference/for-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)