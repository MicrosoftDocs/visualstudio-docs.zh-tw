---
title: "日期和時間字串 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: "47"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="date-and-time-strings-javascript"></a>日期和時間字串 (JavaScript)
您可以使用一些技術來指定和格式化 JavaScript 日期和時間字串。  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>使用 Intl.DateTimeFormat 來格式化日期  
 Internet Explorer 11 開始支援 [Intl.DateTimeFormat 物件](../javascript/reference/intl-datetimeformat-object-javascript.md)，該物件是 [ECMAScript 國際化 API 規格](http://www.ecma-international.org/ecma-402/1.0/)的一部分。 若要格式化日期，您可以直接使用此物件，也可以使用已更新的 [toLocaleDateString 方法 (日期)](../javascript/reference/tolocaledatestring-method-date-javascript.md) 和 [toLocaleTimeString 方法 (日期)](../javascript/reference/tolocaletimestring-method-date-javascript.md) 實作。 [Date 物件](../javascript/reference/date-object-javascript.md)的這些方法會在內部使用 `Intl.DateTimeFormat` 以支援地區設定和其他格式化選項的新選擇性參數。  
  
 下面範例會示範如何使用 `toLocaleDateString` 和 `toLocaleTimeString` 來格式化日期和時間。 傳遞給這些方法的第一個參數是地區設定值 (如 "en-us")。 第二個參數 (如果存在) 則會指定格式化選項，例如工作日的完整格式。  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 如需完整的格式化選項清單，請參閱 [Intl.DateTimeFormat 物件](../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
## <a name="formatting-dates"></a>格式化日期  
 在 Internet Explorer 11 之前，JavaScript 並沒有格式化日期和時間的特定方法。 若要針對舊版瀏覽器提供您自己的日期格式，請使用 [getDay 方法 (日期)](../javascript/reference/getday-method-date-javascript.md)、[getDate 方法 (日期)](../javascript/reference/getdate-method-date-javascript.md)、[getMonth 方法 (日期)](../javascript/reference/getmonth-method-date-javascript.md) 和 [getFullYear 方法 (日期)](../javascript/reference/getfullyear-method-date-javascript.md) 方法  ([getYear 方法 (日期)](../javascript/reference/getyear-method-date-javascript.md) 已經淘汰，不應該予以使用)。  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 您可以使用 [getHours 方法 (日期)](../javascript/reference/gethours-method-date-javascript.md)、[getMinutes 方法 (日期)](../javascript/reference/getminutes-method-date-javascript.md)、[getSeconds 方法 (日期)](../javascript/reference/getseconds-method-date-javascript.md) 和 [getMilliseconds 方法 (日期)](../javascript/reference/getmilliseconds-method-date-javascript.md) 方法來提供自己的時間格式。  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>將字串轉換為日期  
 您可以使用 `Date` 或 `Date(dateStr)` 來指定要建構 `Date.parse(dateStr)` 物件的字串。 JavaScript 使用下列規則剖析日期字串：  
  
-   它會先嘗試使用 [ISO 日期格式](#ISO)來剖析日期字串。  
  
    > [!NOTE]
    >  JavaScript 使用簡化版本的 ISO 8601 擴充格式。  
  
-   如果日期字串不是 ISO 格式，則 JavaScript 會嘗試使用其他[其他日期格式](#OtherDateFormats)來剖析日期。  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>ISO 日期格式  
 ISO 格式是 ISO 8601 擴充格式的簡化。 格式如下：  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  Internet Explorer 8 標準模式和 Quirks 模式不支援 ISO 日期格式。  
  
 下表說明這個格式的各部分。  
  
|符號|描述|值|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|字串中的實際字元。 `T` 指定時間的起始。||  
|`YYYY`|年。 可以使用擴充年份來替代 4 位數年份。 如需詳細資訊，請參閱本主題稍後的[擴充年份](../javascript/date-and-time-strings-javascript.md#bkmk_extend)。||  
|`MM`|月份|01 至 12|  
|`DD`|月份日期|01 至 31|  
|`HH`|小時|00 至 24|  
|`mm`|分鐘|00 至 59|  
|`ss`|秒鐘。 如果有指定時間，則秒鐘和毫秒為選擇性的選項。|00 至 59|  
|`sss`|Milliseconds|00 至 999|  
|`Z`|這個位置的值可以是下列其中一項。 如果省略此值，則會使用 UTC 時間。<br /><br /> -   `Z` 指出 UTC 時間。<br />-   `+hh:mm` 指出輸入時間是 UTC 時間之後的指定位移。<br />-   `-hh:mm` 指出輸入時間是 UTC 時間以前之指定位移的絕對值。||  
  
 此字串只能包含日期，如以下格式所示：`YYYY`、`YYYY-MM`、`YYYY-MM-DD`。  
  
 ISO 格式不支援時區名稱。 您可以使用 `Z` 位置指定與 UTC 時間之間的位移。 如果 `Z` 位置沒有包含值，則會使用 UTC 時間。  
  
 您可以使用 00:00 或是前一天的 24:00 來指定午夜。 下列兩個字串指定的是相同的時間：2010-05-25T00:00 和 2010-05-24T24:00。  
  
 若要傳回 ISO 格式的日期，您可以使用 [toISOString 方法 (日期)](../javascript/reference/toisostring-method-date-javascript.md)。  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>擴充年份  
 「擴充年份」為 6 位數而不是 4 位數，而且前面會加上正號或負號。 `+002010` 是擴充年份的一例，它相當於 `2010`。 您可以使用擴充年份來表示 0 年以前或 9999 年以後的年份。  
  
 如果您使用 6 位數格式，必須有正號或負號。 當您使用 4 位數格式時，不能有正號或負號。 因此，`0000` 和 `+000000` 都可接受，但是 `000000` 和 `-0001` 會產生錯誤。 擴充年份 0 會視為正數，因此會在前面加上正號。  
  
 [toISOString 方法 (日期)](../javascript/reference/toisostring-method-date-javascript.md) 對於 0 以前和 9999 以後的年份一律會使用擴充年份格式。  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>其他日期格式  
 如果日期字串不是使用 ISO 格式，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會使用下列規則進行剖析。  
  
 簡短日期  
  
-   此格式必須遵循月/日/年的順序，例如 "06/08/2010"。  
  
-   "/" 或 "-" 都可用來做為分隔符號。  
  
 完整日期  
  
-   年、月和日可以按照任何順序排列。 "June 8 2010" 和 "2010 June 8" 兩者都有效。  
  
-   年份可以有 2 位數或 4 位數。 如果年份只有兩位數，則必須至少為 70。  
  
-   月份和星期名稱必須至少有兩個字元。 不是唯一的兩個字元名稱會解析為最後一個符合的名稱。 例如，"Ju" 指的是 7 月 (July) 而不是 6 月 (June)。  
  
-   如果一週中的星期名稱與所提供日期的其餘部分不一致，則會予以忽略。 例如，"Tuesday November 9 1996" (1996 年 11 月 9 日星期二) 會解析為 "Friday November 9 1996" (1996 年 11 月 9 日星期五)，因為星期五是該日期的正確星期名稱。  
  
 時間  
  
-   小時、分鐘和秒鐘會以冒號分隔。 但是，可以省略某些部分。 以下是有效的格式："10:"、"10:11" 和 "10:11:12"。  
  
-   如果指定了 PM，而且指定的時數至少為 13，則會傳回 NaN。 例如，"23:15 PM" 會傳回 NaN。  
  
 一般  
  
-   包含無效日期的字串會傳回 NaN。 例如，包含兩個年份或兩個月份的字串會傳回 NaN。  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支援所有標準時區、全球定位時間 (UTC) 和格林威治標準時間 (GMT)  (ISO 格式不支援時區)。  
  
-   括在括號中的文字都會當成註解。 括號可以是巢狀結構。  
  
-   逗號和空格會視為分隔符號。 您可以使用多個分隔符號。  
  
## <a name="example"></a>範例  
 下面程式碼會顯示剖析不同日期和時間字串的結果。  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 當指定本地時間時，結果會因為時區而異。  
  
> [!IMPORTANT]
>  Internet Explorer 8 標準模式和 Quirks 模式不支援 ISO 日期格式。  
  
## <a name="see-also"></a>另請參閱  
 [Date 物件](../javascript/reference/date-object-javascript.md)   
 [Date.parse 函式](../javascript/reference/date-parse-function-javascript.md)