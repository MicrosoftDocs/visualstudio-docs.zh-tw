---
title: "setYear 方法 （日期） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>setYear 方法 (日期) (JavaScript)
設定中的年份值`Date`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>參數  
 `dateObj`  
 必要項。 任何 `Date` 物件。  
  
 `numYear`  
 必要項。 透過 1999年 1900 年，這是數值等於減 1900 年。 超出該範圍的日期，這會是 4 位數的數值。  
  
## <a name="remarks"></a>備註  
 這個方法已過時，而且，為了回溯相容性才提供。 請改用 `setFullYear` 方法。  
  
 若要設定的年份`Date`1997 年物件呼叫**setYear(97)**。 若要設定 2010 年，呼叫**setYear(2010)**。 最後，若要設定為 0-99 的範圍中之年的年份，使用`setFullYear`方法。  
  
> [!NOTE]
>  如[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]1.0 版，`setYear`會使用 1900 所提供的年份值的相加的結果值`numYear`，不論值的年份。 例如，若要設 1899 年`numYear`為-1，並設定 2000 年`numYear`為 100。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [getFullYear 方法 （日期）](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 （日期）](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear 方法 （日期）](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear 方法 （日期）](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)