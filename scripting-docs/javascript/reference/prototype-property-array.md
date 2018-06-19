---
title: prototype 屬性 （陣列） |Microsoft 文件
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd5102fe2f49218de76c498a11256a6ef24ff0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639008"
---
# <a name="prototype-property-array"></a>prototype 屬性 (陣列)
傳回陣列的類別的原型參考。  
  
## <a name="syntax"></a>語法  
  
```  
  
array.prototype  
```  
  
## <a name="remarks"></a>備註  
 `array`引數為陣列的名稱。  
  
 `prototype` 屬性可用來提供某類別物件的一組基本功能。 物件的新執行個體會「繼承」指派給該物件之原型的行為。  
  
 例如，若要將方法加入可傳回陣列中最大項目值的 `Array` 物件，請宣告函式，並將它加入 `Array.prototype`，然後使用它。  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件具有`prototype`是唯讀的屬性。 屬性和方法可能會加入原型，但該物件可能未獲指派不同的原型。 不過，使用者定義的物件可能會指派新的原型。  
  
 語言參考中的每個內建函式物件的方法和屬性清單會指出哪些屬於物件的原型，但並不是。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]