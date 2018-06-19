---
title: getFullYear 方法 （日期） (JavaScript) |Microsoft 文件
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
- getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636748"
---
# <a name="getfullyear-method-date-javascript"></a>getFullYear 方法 (日期) (JavaScript)
取得使用本地時間的年度。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 以四位數表示的年份。 例如，年份 1976年會當成 1976年。 指定為兩位數的年份`Date`建構函式或在`setFullYear`假設為二十一世紀，因此，假設"5/14/12"，`getFullYear`傳回"1912"。  
  
## <a name="remarks"></a>備註  
 若要取得使用國際標準時間 (UTC) 的年份，請使用`getUTCFullYear`方法。  
  
## <a name="example"></a>範例  
 下列範例說明使用**getFullYear**方法。  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getUTCFullYear 方法 （日期）](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 （日期）](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)