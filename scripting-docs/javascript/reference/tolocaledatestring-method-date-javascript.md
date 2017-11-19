---
title: "toLocaleDateString 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaledatestring-method-date-javascript"></a>toLocaleDateString 方法 (日期) (JavaScript)
傳回字串值，適用於主機環境之目前地區設定或指定的地區設定的日期。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 `Date` 物件。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。 一個物件，該物件包含一個或多個指定比較選項的屬性。  
  
## <a name="remarks"></a>備註  
 從 Internet Explorer 11、`toLocaleDateString`使用`Intl.DateTimeFormat`內部要格式化的日期，新增了支援`locales`和`options`參數。 如需有關這些參數的詳細資訊，請參閱[Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  所有文件模式和瀏覽器版本都不支援 `locales` 和 `options` 參數。 如需詳細資訊，請參閱＜需求＞一節。  
  
 以 Internet Explorer 10 標準文件模式、舊版文件模式和快速模式使用 `toLocaleDateString` 時：  
  
-   它會傳回包含目前時區中的日期的字串值。  
  
-   傳回的日期的主機環境之目前地區設定的預設格式。  
  
 如果您省略 `locales` 參數，這個方法的傳回值就不能依賴指令碼，因為它會因電腦不同而相異。 在此案例中，使用的方法只格式化顯示的文字-永遠不會做為計算的一部分。  
  
## <a name="example"></a>範例  
 下列範例示範如何搭配使用 `toLocaleDateString` 方法與指定的地區設定和比較選項。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toDateString 方法 （日期）](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)