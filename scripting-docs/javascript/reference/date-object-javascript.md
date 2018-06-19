---
title: Date 物件 (JavaScript) |Microsoft 文件
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
- Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641928"
---
# <a name="date-object-javascript"></a>Date 物件 (JavaScript)
啟用日期和時間的基本儲存和擷取。  
  
## <a name="syntax"></a>語法  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 要對其指派 `Date` 物件的變數名稱。  
  
 `dateVal`  
 必要項。 如果數字，`dateVal`表示的格式為國際標準時間介於指定的日期和 1970 年 1 月 1 日午夜起的毫秒數。 如果是字串，`dateVal`剖析根據中的規則[日期和時間字串](../../javascript/date-and-time-strings-javascript.md)。 `dateVal`引數也可以 VT_DATE 值傳回的某些 ActiveX 物件。  
  
 `year`  
 必要項。 完整的年份，比方說，1976年 （和不 76）。  
  
 `month`  
 必要項。 介於 0 到 11 （一月至十二月） 的整數，表示月份。  
  
 `date`  
 必要項。 介於 1 到 31 之間的整數日期。  
  
 `hours`  
 選擇項。 如果必須提供`minutes`提供。 從 0 到 23 （午夜到下午 11 點） 的整數，指定在一小時。  
  
 分鐘  
 選擇項。 如果必須提供`seconds`提供。 指定的整數從 0 到 59 分鐘的時間。  
  
 `seconds`  
 選擇項。 如果必須提供`milliseconds`提供。 指定的整數從 0 到 59 的秒數。  
  
 `ms`  
 選擇項。 從 0 到 999 的整數來指定毫秒數。  
  
## <a name="remarks"></a>備註  
 A`Date`物件包含代表特定的即時時間以毫秒的數字。 如果引數的值大於它的範圍，或為負數，就會據以修改其他的儲存的值。 例如，如果您指定 150 秒，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]重新該數字將定義為兩分鐘到 30 秒。  
  
 如果數值為`NaN`，物件不代表特定時間的瞬間。 如果您沒有傳遞參數至`Date`物件，它會初始化為目前時間 (UTC)。 您可以使用它之前，必須指定值物件。  
  
 可以用來表示的日期範圍`Date`物件是從 1970 年 1 月 1 日的任一端大約 285616 年。  
  
 請參閱[計算日期和時間 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)如需有關如何使用`Date`物件及相關的方法。  
  
## <a name="example"></a>範例  
 以下範例將示範 `Date` 物件的用法。  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>需求  
 `Date object` 已在 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] 中引入。 下列清單中的某些成員是在後來的版本中才導入。 如需詳細資訊，請參閱[版本資訊](../../javascript/reference/javascript-version-information.md)或個別成員的文件集。  
  
## <a name="properties"></a>屬性  
 以下資料表列出 `Date Object` 的屬性。  
  
|屬性|說明|  
|--------------|-----------------|  
|[constructor 屬性](../../javascript/reference/constructor-property-date.md)|指定用來建立物件的函式。|  
|[prototype 屬性](../../javascript/reference/prototype-property-date.md)|傳回物件類別的原型參考。|  
  
## <a name="functions"></a>函式  
 以下資料表列出 `Date Object` 的函式。  
  
|函式|說明|  
|---------------|-----------------|  
|[Date.now 函式](../../javascript/reference/date-now-function-javascript.md)|傳回 1970 年 1 月 1 日之間的毫秒數字及目前的日期和時間。|  
|[Date.parse 函式](../../javascript/reference/date-parse-function-javascript.md)|剖析字串，包含日期，並傳回該日期和從 1970 年 1 月 1 日午夜之間的毫秒數。|  
|[Date.UTC 函式](../../javascript/reference/date-utc-function-javascript.md)|傳回從 1970 年 1 月 1 日午夜之間的毫秒數國際標準時間 (UTC) （或 GMT） 指定的日期。|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>方法  
 以下資料表列出 `Date Object` 的方法。  
  
|方法|說明|  
|------------|-----------------|  
|[getDate 方法](../../javascript/reference/getdate-method-date-javascript.md)|傳回使用本地時間的月份日期值。|  
|[getDay 方法](../../javascript/reference/getday-method-date-javascript.md)|傳回使用本地時間的週日期值。|  
|[getFullYear 方法](../../javascript/reference/getfullyear-method-date-javascript.md)|傳回使用本地時間的年份值。|  
|[getHours 方法](../../javascript/reference/gethours-method-date-javascript.md)|傳回使用本地時間的小時值。|  
|[getMilliseconds 方法](../../javascript/reference/getmilliseconds-method-date-javascript.md)|傳回使用本地時間的毫秒值。|  
|[getMinutes 方法](../../javascript/reference/getminutes-method-date-javascript.md)|傳回使用本地時間的分鐘值。|  
|[getMonth 方法](../../javascript/reference/getmonth-method-date-javascript.md)|傳回使用本地時間的月份值。|  
|[getSeconds 方法](../../javascript/reference/getseconds-method-date-javascript.md)|傳回使用本地時間的秒數值。|  
|[getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)|傳回時間值`Date`物件做為從 1970 年 1 月 1 日午夜起的毫秒數。|  
|[getTimezoneOffset 方法](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|傳回主機電腦上的時間與國際標準時間 (UTC) 之間的差異以分鐘為單位。|  
|[getUTCDate 方法](../../javascript/reference/getutcdate-method-date-javascript.md)|傳回使用 UTC 的月份日期值。|  
|[getUTCDay 方法](../../javascript/reference/getutcday-method-date-javascript.md)|傳回使用 UTC 的星期日期值。|  
|[getUTCFullYear 方法](../../javascript/reference/getutcfullyear-method-date-javascript.md)|傳回使用 UTC 的年份值。|  
|[getUTCHours 方法](../../javascript/reference/getutchours-method-date-javascript.md)|傳回使用 UTC 的小時值。|  
|[getUTCMilliseconds 方法](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|傳回使用 UTC 毫秒值。|  
|[getUTCMinutes 方法](../../javascript/reference/getutcminutes-method-date-javascript.md)|傳回使用 UTC 的分鐘值。|  
|[getUTCMonth 方法](../../javascript/reference/getutcmonth-method-date-javascript.md)|傳回使用 UTC 的月份值。|  
|[getUTCSeconds 方法](../../javascript/reference/getutcseconds-method-date-javascript.md)|傳回秒數值使用 UTC。|  
|[getVarDate 方法](../../javascript/reference/getvardate-method-date-javascript.md)|傳回在 VT_DATE 值`Date`物件。|  
|[getYear 方法](../../javascript/reference/getyear-method-date-javascript.md)|傳回年份值。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|傳回布林值，表示物件是否具有指定名稱的屬性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|傳回布林值，表示物件是否存在於另一個物件的原型鏈結中。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|傳回布林值，表示指定的屬性是否為物件的一部分，以及是否可以列舉。|  
|[setDate 方法](../../javascript/reference/setdate-method-date-javascript.md)|設定數字使用本地時間的月份天數。|  
|[setFullYear 方法](../../javascript/reference/setfullyear-method-date-javascript.md)|設定使用本地時間的年份值。|  
|[setHours 方法](../../javascript/reference/sethours-method-date-javascript.md)|設定使用本地時間的小時值。|  
|[setMilliseconds 方法](../../javascript/reference/setmilliseconds-method-date-javascript.md)|設定使用本地時間的毫秒值。|  
|[setMinutes 方法](../../javascript/reference/setminutes-method-date-javascript.md)|設定使用本地時間的分鐘值。|  
|[setMonth 方法](../../javascript/reference/setmonth-method-date-javascript.md)|設定使用本地時間的月份值。|  
|[setSeconds 方法](../../javascript/reference/setseconds-method-date-javascript.md)|設定秒數值使用本地時間。|  
|[setTime 方法](../../javascript/reference/settime-method-date-javascript.md)|設定中的日期和時間值`Date`物件。|  
|[setUTCDate 方法](../../javascript/reference/setutcdate-method-date-javascript.md)|設定每一天的月份使用 UTC。|  
|[setUTCFullYear 方法](../../javascript/reference/setutcfullyear-method-date-javascript.md)|設定使用 UTC 的年份值。|  
|[setUTCHours 方法](../../javascript/reference/setutchours-method-date-javascript.md)|設定使用 UTC 的小時值。|  
|[setUTCMilliseconds 方法](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|設定使用 UTC 毫秒值。|  
|[setUTCMinutes 方法](../../javascript/reference/setutcminutes-method-date-javascript.md)|設定使用 UTC 的分鐘值。|  
|[setUTCMonth 方法](../../javascript/reference/setutcmonth-method-date-javascript.md)|設定使用 UTC 的月份值。|  
|[setUTCSeconds 方法](../../javascript/reference/setutcseconds-method-date-javascript.md)|設定秒數值使用 UTC。|  
|[setYear 方法](../../javascript/reference/setyear-method-date-javascript.md)|設定使用本地時間的年份值。|  
|[toDateString 方法](../../javascript/reference/todatestring-method-date-javascript.md)|傳回字串值的日期。|  
|[toGMTString 方法](../../javascript/reference/togmtstring-method-date-javascript.md)|傳回將日期轉換成使用格林威治標準時間 (GMT) 的字串。|  
|[toISOString 方法](../../javascript/reference/toisostring-method-date-javascript.md)|傳回 ISO 格式的日期字串值。|  
|[toJSON 方法](../../javascript/reference/tojson-method-date-javascript.md)|用來轉換資料之前 JSON 序列化的物件型別。|  
|[toLocaleDateString 方法](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|傳回主機環境之目前地區設定適當的日期字串值。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-date.md)|傳回轉換成字串，使用目前的地區設定的物件。|  
|[toLocaleTimeString 方法](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|傳回字串值的時間適用於主機環境之目前地區設定。|  
|[toString 方法](../../javascript/reference/tostring-method-date.md)|傳回物件的字串表示。|  
|[toTimeString 方法](../../javascript/reference/totimestring-method-date-javascript.md)|傳回字串值的時間。|  
|[toUTCString 方法](../../javascript/reference/toutcstring-method-date-javascript.md)|傳回轉換成字串，使用 UTC 日期。|  
|[valueOf 方法](../../javascript/reference/valueof-method-date.md)|傳回指定物件的基本值。|  
  
## <a name="see-also"></a>另請參閱  
 [計算日期和時間 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [日期和時間字串](../../javascript/date-and-time-strings-javascript.md)