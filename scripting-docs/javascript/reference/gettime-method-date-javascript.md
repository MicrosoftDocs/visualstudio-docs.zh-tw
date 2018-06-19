---
title: getTime 方法 （日期） (JavaScript) |Microsoft 文件
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
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636658"
---
# <a name="gettime-method-date-javascript"></a>getTime 方法 (日期) (JavaScript)
取得時間值以毫秒為單位。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回從 1970 年 1 月 1 日午夜和時間值之間的毫秒數`Date`物件。 日期範圍是從 1970 年 1 月 1 日午夜的任一端大約 285616 年。 負數表示在 1970 年之前的日期。  
  
## <a name="remarks"></a>備註  
 在執行多個日期和時間的計算時，您可以定義等於的毫秒數的變數中的日、 小時或分鐘。 例如:   
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 請參閱[計算日期和時間 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)如需有關如何使用`getTime`方法。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `getTime` 方法。  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [setTime 方法 (Date)](../../javascript/reference/settime-method-date-javascript.md)