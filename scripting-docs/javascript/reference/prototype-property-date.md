---
title: "prototype 屬性 （日期） |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>prototype 屬性 (日期)
傳回日期的原型參考。  
  
## <a name="syntax"></a>語法  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>備註  
 `date` 引數是物件的名稱。  
  
 使用`prototype`屬性提供一組基本功能的日期。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入可傳回陣列中最大項目值的 `Date` 物件，請宣告函式，並將它加入 `Date.prototype`，然後使用它。  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件具有`prototype`是唯讀的屬性。 屬性和方法可能會加入原型，但該物件可能未獲指派不同的原型。 不過，使用者定義的物件可能會指派新的原型。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]