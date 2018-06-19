---
title: 使用陣列 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569158"
---
# <a name="using-arrays-javascript"></a>使用陣列 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的陣列是「鬆散的」。 也就是說，如果您有編號 0、1 和 2 三個元素的陣列，您可以建立元素 50，不用擔心元素 3 到 49。 如果陣列中有自動長度變數 (請參閱[內建物件](../../javascript/intrinsic-objects-javascript.md)取得自動監視陣列長度的說明)，長度變數要設為 51，不是 4。 您可以建立元素編號無間距的陣列，但沒必要這麼做。  
  
 在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中，物件和陣列彼此幾乎完全相同。 兩項主要的差異是，非陣列物件沒有自動長度屬性，而陣列沒有物件的屬性和方法。  
  
## <a name="addressing-arrays"></a>定址陣列  
 您可以使用括弧 ([]) 定址陣列，如下列範例所示。 括弧會括住數值或評估為整數的運算式。  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>當作關聯陣列的物件  
 點運算子 "." 通常用來存取物件的屬性。 例如：  
  
```JavaScript  
myObject.aProperty  
```  
  
 本例的屬性名稱是識別碼。 您也可以使用索引運算子 ([]) 來存取物件的屬性。 在本例中，您將物件視為資料值與字串建立關聯的*關聯陣列*。 例如：  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 索引運算子更常與存取陣列元素建立關聯。 搭配物件使用時，索引是表示屬性名稱的字串常值。  
  
 請注意，兩種物件屬性存取方式之間的重要差異。  
  
1.  視同識別碼的屬性名稱 (點 (.) 語法)，無法像資料一樣操作。  
  
2.  視同索引的屬性名稱 (括弧 ([]) 語法)，無法像資料一樣操作。  
  
 當您要等到執行階段才知道屬性名稱是什麼時，此差異就變得很有用 (例如，要根據使用者輸入建構物件時)。 若要擷取關聯陣列中的所有屬性，您必須使用 `for...in` 迴圈。