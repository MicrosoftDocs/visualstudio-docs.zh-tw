---
title: "Intl.NumberFormat 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat 物件 (JavaScript)
提供地區設定特定的數字格式。  
  
## <a name="syntax"></a>語法  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>參數  
 `numberFormatObj`  
 必要項。 要指派 `NumberFormat` 物件的變數名稱。  
  
 `locales`  
 選擇項。 包含一個或多個語言或地區設定標記的地區設定字串的陣列。 如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。 如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `options`  
 選擇項。 物件，其中包含一或多個指定數字格式選項的屬性。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 `locales`參數必須符合[BCP 47](http://tools.ietf.org/html/rfc5646)語言或地區設定標記，例如"EN-US"和"ZH-CN"。 此標記可能包括語言、國家/地區和變化。 例如語言標記的詳細資訊，請參閱[附錄 A](http://tools.ietf.org/html/rfc5646#appendix-A)的 BCP 47。 如`NumberFormat`，您可以新增**-u**子標記後面-兵指定編號的系統擴充功能：  
  
 「*語言*-*區域*-u-兵-*numberingsystem*"  
  
 其中*numberingsystem*可能是下列其中之一： 阿拉伯、 arabext、 bali、 beng、 deva、 fullwide、 gujr、 專家、 hanidec、 khmr、 knda、 laoo、 latn、 恙、 mylm、 旺、 mymr、 orya、 tamldec、 telu、 泰文、 tibt。  
  
 `options` 參數可以包含下列屬性：  
  
|屬性|描述|可能的值|預設值|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|指定要使用的地區設定比對演算法。|"lookup"、"best fit"|"best fit"|  
|`style`|指定的數字的格式樣式。|「 小 」，「 百分比 」，[貨幣]|「 小數點 」|  
|`currency`|指定的 ISO 4217 貨幣值，以字母代碼。 如果`style`設為 「 貨幣 」，這是必要值。|請參閱 ISO[貨幣和資金程式碼清單](http://www.currency-iso.org/en/home/tables/table-a1.html)。|未定義|  
|`currencyDisplay`|指定是否要顯示之貨幣的 ISO 4217 貨幣字母代碼，當地語系化的貨幣符號，或當地語系化的貨幣名稱。 會使用此值，只有當`style`設為 [貨幣]。|「 程式碼 」、 「 符號 」、 「 名稱 」|「 符號 」|  
|`useGrouping`|指定是否應使用群組分隔符號。|true、 false|`true`.|  
|`minimumIntegerDigits`|指定要使用的整數位數的最小數目。|1 到 21。|21|  
|`minimumFractionDigits`|。 指定要使用的小數點後數字的最小數目。|0 到 20。|0|  
|`maximumFractionDigits`|指定要使用的小數點後數字的數目上限。|這個值可以介於`minimumFractionDigits`為 20。|20.|  
|`minimumSignificantDigits`|指定要顯示小數點後數字的最小數目。|此值範圍從 1 到 21。|1|  
|`maximumSignificantDigits`|指定要顯示的小數位數的數目上限。|這個值可以介於`minimumSignificantDigits`為 21。|21|  
  
## <a name="properties"></a>屬性  
 下表列出 `NumberFormat` 物件的屬性。  
  
|||  
|-|-|  
|屬性|說明|  
|[建構函式](../../javascript/reference/constructor-property-intl-numberformat.md)|指定的函式，會建立數字的格式子物件。|  
|[<格式>](../../javascript/reference/format-property-intl-numberformat.md)|傳回函數，使用數字的格式器設定格式化數字。|  
|[原型](../../javascript/reference/prototype-property-intl-numberformat.md)|傳回數字的格式子的原型參考。|  
  
## <a name="methods"></a>方法  
 下表列出 `NumberFormat` 物件的方法。  
  
|||  
|-|-|  
|方法|說明|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|傳回包含的屬性和值的數字的格式子物件的物件。|  
  
## <a name="example"></a>範例  
 下列範例會建立`NumberFormat`EN-US 地區設定所指定的格式設定選項的物件。  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>範例  
 下列範例顯示使用數個不同的地區設定和選項的結果。  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [toLocaleString （數字）](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)