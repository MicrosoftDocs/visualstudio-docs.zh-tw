---
title: format 屬性 (Intl.DateTimeFormat) |Microsoft 文件
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636588"
---
# <a name="format-property-intldatetimeformat"></a>format 屬性 (Intl.DateTimeFormat)
傳回使用指定的日期/時間格式器設定來格式化地區設定特定日期的函式。  
  
## <a name="syntax"></a>語法  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>參數  
 `dateTimeFormatObj`  
 必要項。 名稱`DateTimeFormat`做為格式子物件。  
  
## <a name="remarks"></a>備註  
 所傳回的函式`format`屬性會接受單一引數， `date`，並傳回字串，代表使用指定的選項的當地語系化的日期`DateTimeFormat`物件。 `date`傳回的函式的參數必須是數字、 日期字串或`Date`物件。 如果`date`未提供，此函數會使用[Date.now](../../javascript/reference/date-now-function-javascript.md)做為預設的輸入值。  
  
## <a name="example"></a>範例  
 下列範例會使用`DateTimeFormat`當地語系化成德文的日期 「 2007 年 12 月 1 日 」，並將它重新格式化的物件。  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)