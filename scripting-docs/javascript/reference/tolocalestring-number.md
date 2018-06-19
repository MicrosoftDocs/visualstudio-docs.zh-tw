---
title: toLocaleString （數字） |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640828"
---
# <a name="tolocalestring-number"></a>toLocaleString (數字)
將數字轉換為字串所使用的目前或指定的地區設定。  
  
## <a name="syntax"></a>語法  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>參數  
 `numberObj`  
 必要項。 `Number`来轉換的物件。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。 一個物件，該物件包含一個或多個指定比較選項的屬性。  
  
## <a name="remarks"></a>備註  
 從 Internet Explorer 11、`toLocaleString`使用`Intl.NumberFormat`在內部以進行比較，新增了支援`locales`和`options`參數。 如需有關這些參數的詳細資訊，請參閱[Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  所有文件模式和瀏覽器版本都不支援 `locales` 和 `options` 參數。 如需詳細資訊，請參閱＜需求＞一節。  
  
> [!NOTE]
>  如果您省略`locales`參數，使用`toLocaleString`只用來顯示結果的使用者; 永遠不會使用它來計算值中使用指令碼，因為傳回的結果是電腦專屬 （此方法會傳回目前的地區設定）。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`toLocaleString`不含任何參數的方法。  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何搭配使用 `toLocaleString` 方法與指定的地區設定和比較選項。  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)