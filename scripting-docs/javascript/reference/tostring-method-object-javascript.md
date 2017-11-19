---
title: "toString 方法 (Object) (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>toString 方法 (Object) (JavaScript)
傳回物件的字串表示。  
  
## <a name="syntax"></a>語法  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>參數  
 `objectname`  
 必要項。 要尋找的字串表示的物件。  
  
 `radix`  
 選擇項。 指定將數值轉換為字串的基數。 這個值只用於數字。  
  
## <a name="remarks"></a>備註  
 **ToString**方法所屬的所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件。 它的行為取決於物件類型：  
  
|物件|行為|  
|------------|--------------|  
|陣列|項目`Array`轉換為字串。 產生的字串串連，以逗號分隔。|  
|Boolean|如果布林值為**true**，傳回"`true`"。 反之則傳回"`false`"。|  
|日期|傳回日期的文字表示。|  
|錯誤|傳回包含相關聯的錯誤訊息的字串。|  
|函式|傳回下列格式的字串，其中*functionname*函式名稱的**toString**方法呼叫：<br /><br /> `function functionname( ) { [native code] }`|  
|數字|傳回數字的文字表示。|  
|String|傳回的值`String`物件。|  
|預設|傳回`"[object objectname]"`，其中`objectname`是物件類型的名稱。|  
  
## <a name="example"></a>範例  
 下列範例說明使用**toString**基數引數的方法。 如下所示的函式的傳回值是基數轉換資料表。  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **適用於**: [Array 物件](../../javascript/reference/array-object-javascript.md)&#124;[Boolean 物件](../../javascript/reference/boolean-object-javascript.md)&#124;[日期物件](../../javascript/reference/date-object-javascript.md)&#124;[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)&#124;[函式物件](../../javascript/reference/function-object-javascript.md)&#124;[編號物件](../../javascript/reference/number-object-javascript.md)&#124;[物件物件](../../javascript/reference/object-object-javascript.md)&#124;[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)