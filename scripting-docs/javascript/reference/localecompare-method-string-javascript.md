---
title: localeCompare 方法 （字串） (JavaScript) |Microsoft 文件
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
- localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639548"
---
# <a name="localecompare-method-string-javascript"></a>localeCompare 方法 (字串) (JavaScript)
判斷兩個字串中目前的地區設定是否相等。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>參數  
 `stringVar`  
 必要項。 要比較的第一個字串。  
  
 `stringExp`  
 必要項。 要比較的第二個字串。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。 這個參數必須符合[BCP 47](http://tools.ietf.org/html/rfc5646)標準，請參閱 < [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)如需詳細資訊。  
  
 `options`  
 選擇項。 一個物件，該物件包含一個或多個指定比較選項的屬性。 請參閱[Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)如需詳細資訊。  
  
## <a name="remarks"></a>備註  
 比較字串，您可能會指定`String`物件或字串常值。  
  
 從 Internet Explorer 11、`localeCompare`使用`Intl.Collator`物件在內部進行比較，這樣會將支援`locales`和`options`參數。 如需有關這些參數的詳細資訊，請參閱[Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)和[Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md)。  
  
> [!IMPORTANT]
>  所有文件模式和瀏覽器版本都不支援 `locales` 和 `options` 參數。 如需詳細資訊，請參閱＜需求＞一節。  
  
 `localeCompare`方法執行區分地區設定特性的字串比較的`stringVar`和`stringExp`並傳回下列其中一種結果的排序順序，系統預設地區設定而定：  
  
-   -1，否則`stringVar`之前`stringExp`。  
  
-   + 1，否則`stringVar`之後排序`stringExp`。  
  
-   0 （零） （如果兩個字串相等。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`localeCompare`。  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`localeCompare`德文 （德國） 地區設定。  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`localeCompare`德文 （德國） 地區設定與指定德文電話簿的排序次序的地區設定特定延伸模組。 此範例示範地區設定特定的差異。  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleString 方法 (Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)