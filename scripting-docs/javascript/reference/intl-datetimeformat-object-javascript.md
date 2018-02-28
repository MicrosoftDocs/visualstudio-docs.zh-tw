---
title: "Intl.DateTimeFormat 物件 (JavaScript) |Microsoft 文件"
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
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat 物件 (JavaScript)
提供地區設定特定的日期和時間格式。  
  
## <a name="syntax"></a>語法  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>參數  
 `dateTimeFormatObj`  
 必要項。 要指派 `DateTimeFormat` 物件的變數名稱。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `options`  
 選擇項。 一個物件，該物件包含一個或多個指定日期和時間之格式化選項的屬性。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 `locales`參數必須符合[BCP 47](http://tools.ietf.org/html/rfc5646)語言或地區設定標記，例如"EN-US"和"ZH-CN"。 此標記可能包括語言、國家/地區和變化。 例如語言標記的詳細資訊，請參閱[附錄 A](http://tools.ietf.org/html/rfc5646#appendix-A)的 BCP 47。 如`DateTimeFormat`，您可以新增**-u**子標記的地區設定字串中要包含一個或兩個下列 Unicode 延伸：  
  
-   -指定編號的系統延伸兵：*語言*-*區域*-u-兵-*numberingsystem*  
  
     其中*numberingsystem*可能是下列其中之一： 阿拉伯、 arabext、 bali、 beng、 deva、 fullwide、 gujr、 專家、 hanidec、 khmr、 knda、 laoo、 latn、 恙、 mylm、 旺、 mymr、 orya、 tamldec、 telu、 泰文、 tibt。  
  
-   若要指定行事曆 ca:*語言*-*區域*-u-ca-*行事曆*  
  
     其中*行事曆*可能是下列其中之一： 佛教、 中文、 gregory 伊斯蘭、 islamicc、 日文。  
  
 `options` 參數可以包含下列屬性：  
  
|屬性|描述|可能的值|預設值|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|指定要使用的地區設定比對演算法。|"lookup"、"best fit"|"best fit"|  
|`formatMatcher`|指定要使用的格式比對演算法。|"basic"、"best fit"|"best fit"|  
|`hour12`|指定是否使用 12 小時制來表示小時。|`true` (適用於 12 小時制)，`false` (適用於 24 小時制)||  
|`timeZone`|指定時區。 至少永遠支援 "UTC"。|時區值，例如 "UTC"。|"UTC"|  
|`weekday`|指定工作日的格式。|"narrow"、"short"、"long"。|未定義|  
|`era`|指定紀元的格式。|"narrow"、"short"、"long"|未定義|  
|`year`|指定年份的格式。|"2-digit"、"numeric"|未定義或 "numeric"|  
|`month`|指定月份的格式。|"2-digit"、"numeric"、"narrow"、"short"、"long"|未定義或 "numeric"|  
|`day`|指定日期的格式。|"2-digit"、"numeric"|未定義或 "numeric"|  
|`hour`|指定小時的格式。|"2-digit"、"numeric"|未定義|  
|`minute`|指定分鐘的格式。|"2-digit"、"numeric"|未定義|  
|`second`|指定秒鐘的格式。|"2-digit"、"numeric"|未定義|  
|`timeZoneName`|指定時區的格式。 這個屬性目前不支援。|"short"、"long"。|這個屬性目前不支援。|  
  
 `weekday`、`era`、`year`、`month`、`day`、`hour`、`minute` 和 `second` 的預設值為 `undefined`。 如果沒有設定這些屬性，`year`、`month` 和 `day` 會使用「數字」格式。  
  
 每個地區設定都至少必須支援下列格式：  
  
-   weekday, year, month, day, hour, minute, second  
  
-   weekday, year, month, day  
  
-   year, month, day  
  
-   year, month  
  
-   month, day  
  
-   hour, minute, second  
  
-   hour, minute  
  
## <a name="properties"></a>屬性  
 下表列出 `DateTimeFormat` 物件的屬性。  
  
|||  
|-|-|  
|屬性|說明|  
|[建構函式](../../javascript/reference/constructor-property-intl-datetimeformat.md)|指定用來建立日期/時間格式子物件的函式。|  
|[<格式>](../../javascript/reference/format-property-intl-datetimeformat.md)|傳回函式，該函式會透過使用日期/時間格式子設定，來格式化地區設定特定的日期。|  
|[原型](../../javascript/reference/prototype-property-intl-datetimeformat.md)|傳回日期/時間格式子的原型參考。|  
  
## <a name="methods"></a>方法  
 下表列出 `DateTimeFormat` 物件的方法。  
  
|||  
|-|-|  
|方法|說明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|傳回物件，其中包含日期/時間格式子物件的屬性和值。|  
  
## <a name="example"></a>範例  
 下面範例會示範使用不同的地區設定，將日期物件傳遞至 `DateTimeFormat` 的結果。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>範例  
 下面範例會建立 `DateTimeFormat` 物件，使用阿拉伯文 (沙烏地阿拉伯) 地區設定、伊斯蘭曆法和拉丁數字系統，以長格式指定目前的工作日。  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleString （日期）](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString 方法 （日期）](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 （日期）](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat 物件](../../javascript/reference/intl-numberformat-object-javascript.md)