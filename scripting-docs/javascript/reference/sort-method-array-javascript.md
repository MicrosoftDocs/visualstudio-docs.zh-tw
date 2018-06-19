---
title: sort 方法 （陣列） (JavaScript) |Microsoft 文件
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987811"
---
# <a name="sort-method-array-javascript"></a>sort 方法 (陣列) (JavaScript)
排序`Array`。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要。 任何 `Array` 物件。  
  
 `sortFunction`  
 選擇性。 用來判斷項目的順序的函數名稱。 如果省略，則元素以遞增，ASCII 字元順序排序。  
  
## <a name="return-value"></a>傳回值  
 已排序的陣列。  
  
## <a name="remarks"></a>備註  
 `sort`方法來排序`Array`就地物件; 否新`Array`執行期間建立物件。  
  
 `sortFunction`會採用兩個引數，而且必須傳回下列值之一：  
  
-   負值 （小於 0） 的第一個引數傳遞是否小於第二個引數比。  較低的索引來排序第一個引數。
  
-   零 (0) (如果是相等的兩個引數。  兩個引數排序相對於陣列中其他項目，但不是會相對於其他排序。
  
-   （大於 0） 的第一個引數是否大於第二個引數的正數值。  第二個引數排序較低的索引。
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `sort` 方法。  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]