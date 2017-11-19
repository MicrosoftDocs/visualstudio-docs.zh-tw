---
title: "toLocaleString （日期） |Microsoft 文件"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-date"></a>toLocaleString (日期)
將日期轉換成字串，所使用的目前或指定的地區設定。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 `Date`来轉換的物件。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。 一個物件，該物件包含一個或多個指定比較選項的屬性。  
  
## <a name="remarks"></a>備註  
 從 Internet Explorer 11、`toLocaleString`使用`Intl.DateTimeFormat`在內部以進行比較，新增了支援`locales`和`options`參數。 如需有關這些參數的詳細資訊，請參閱[Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  所有文件模式和瀏覽器版本都不支援 `locales` 和 `options` 參數。 如需詳細資訊，請參閱＜需求＞一節。  
  
 以 Internet Explorer 10 標準文件模式、舊版文件模式和快速模式使用 `toLocaleString` 時：  
  
-   它會傳回`String`物件，其中包含寫入目前的地區設定長的預設格式的日期。  
  
-   1999 西元 1601年之間的日期，根據使用者的控制台中的地區設定格式化的日期。  
  
> [!NOTE]
>  如果您省略`locales`參數，使用`toLocaleString`只用來顯示結果的使用者; 永遠不會使用它來計算值中使用指令碼，因為傳回的結果是電腦專屬。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `toLocaleString` 方法。  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何搭配使用 `toLocaleString` 方法與指定的地區設定和比較選項。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)