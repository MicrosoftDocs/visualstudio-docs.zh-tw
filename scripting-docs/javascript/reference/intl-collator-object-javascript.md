---
title: "Intl.Collator 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator 物件 (JavaScript)
提供地區設定特定的字串比較。  
  
## <a name="syntax"></a>語法  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>參數  
 `collatorObj`  
 必要項。 要指派 `Collator` 物件的變數名稱。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `options`  
 選擇項。 一個物件，該物件包含一個或多個指定比較選項的屬性。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 `locales`參數必須符合[BCP 47](http://tools.ietf.org/html/rfc5646)語言或地區設定標記，例如"EN-US"和"Hans-ZH-CN"。 此標記可能包括語言、國家/地區和變化。 如需語言的清單，請參閱[IANA 語言子標記登錄](http://go.microsoft.com/fwlink/p/?linkid=227303)。 例如語言標記的詳細資訊，請參閱[附錄 A](http://tools.ietf.org/html/rfc5646#appendix-A)的 BCP 47。 如`Collator`，您可能會指定一或多個下列 Unicode 延伸地區設定字串中加入-u 延伸模組：  
  
-   指定變數的定序 （地區設定特定）-co:"*語言*-*區域*-u-co-*值*"。  
  
-   指定數值比較-kn:"*語言*-*區域*為 kn-u true &#124; false"。  
  
-   -指定是否要先排序大寫或小寫字元 kf:"*語言*-*區域*-u-kf-上限 &#124;較低 &#124; false")。 目前不支援這項擴充功能。  
  
 若要指定數值比較，您可以在地區設定字串中設定-kn 延伸模組，或使用`numeric`屬性`options`參數。 如果您使用`numeric`屬性，-kn 值將不會套用。  
  
 `options` 參數可以包含下列屬性：  
  
-   `localeMatcher`. 指定要使用的地區設定比對演算法。 可能的值為"lookup"和"best fit"。 預設值是 「 適合 」。  
  
-   `usage`. 指定比較的目標是在排序或搜尋。 可能的值為 「 排序 」 和 「 搜尋 」。 預設值是 「 排序 」。  
  
-   `sensitivity`. 指定自動分頁的敏感度。 可能的值為 「 基底 」、 「 腔調字 」 」 實例"和"variant"。 預設值是 `undefined`。  
  
-   `ignorePunctuation`. 指定是否忽略標點符號的比較中。 可能的值為"true"和"false"。 預設值是 `false`。  
  
-   `numeric`. 指定是否使用數值排序。 可能的值為"true"和"false"。 預設值是 `false`。  
  
-   `caseFirst`. 目前不支援。  
  
## <a name="properties"></a>屬性  
 下表列出 `Collator` 物件的屬性。  
  
|||  
|-|-|  
|屬性|說明|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|傳回函數，比較兩個字串，使用 自動分頁器的排序次序。|  
|[建構函式](../../javascript/reference/constructor-property-intl-collator.md)|指定自動分頁器所建立的函數。|  
|[原型](../../javascript/reference/prototype-property-intl-collator.md)|自動分頁器傳回的原型參考。|  
  
## <a name="methods"></a>方法  
 下表列出 `Collator` 物件的方法。  
  
|||  
|-|-|  
|方法|說明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|傳回物件，包含的屬性和自動分頁器的值。|  
  
## <a name="example"></a>範例  
 下列範例會建立`Collator`物件，並執行的比較。  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>範例  
 下列範例會使用`Collator`排序陣列的物件。 此範例示範地區設定特定的差異。  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會使用`Collator`来搜尋的字串物件，並指定比較選項。  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [localeCompare 方法 （字串）](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat 物件](../../javascript/reference/intl-numberformat-object-javascript.md)