---
title: getYear 方法 （日期） (JavaScript) |Microsoft 文件
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
- getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637078"
---
# <a name="getyear-method-date-javascript"></a>getYear 方法 (日期) (JavaScript)
取得的年份`Date`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## <a name="return-value"></a>傳回值  
 傳回年份。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  這個方法已過時，並提供回溯相容性。 請改用 `getFullYear` 方法。  
  
 在[!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]，然後在 Internet Explorer 版本開始[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]，傳回的值是 1900年減去預存的年份。 例如，1899 年則傳回-1，2000 年，則傳回 100。  
  
 在[!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)]透過[!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]，公式取決於該年份。 透過 1999年 1900 年傳回的值是 2 位數值減去 1900年的預存的年份。 該範圍外的日期，則會傳回 4 位數的年份。 例如，1996年會傳回 96，但現狀傳回 1825年和 2025年。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getFullYear 方法 （日期）](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 （日期）](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 （日期）](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 （日期）](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear 方法 (Date)](../../javascript/reference/setyear-method-date-javascript.md)