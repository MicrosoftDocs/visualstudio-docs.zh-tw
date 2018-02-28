---
title: "length 屬性 （陣列） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-array-javascript"></a>length 屬性 (Array) (JavaScript)
取得或設定陣列的長度。 這是比陣列所定義最高項目高一的數字。  
  
## <a name="syntax"></a>語法  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>參數  
 `numVar`  
 必要項。 任何數字。  
  
 `arrayObj`  
 必要項。 任何 `Array` 物件。  
  
## <a name="remarks"></a>備註  
 在 JavaScript 中，陳列是疏鬆的，陣列中的項目不必連續。 `length` 屬性不一定是陣列中的項目數。 例如，在下列陣列定義中，`my_array.length` 包含 7，不包含 2：  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 如果您讓 `length` 屬性小於其先前的值，陣列會被截斷，並且陣列索引等於或大於 `length` 屬性新值的任何項目都會遺失。  
  
 如果您讓長度屬性大於先前的值， 陣列會展開，且任何建立的新項目都會具有 `undefined` 值。  
  
 下面範例會說明 `length` 屬性的使用：  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  從 Internet Explorer 9 標準模式開始，陣列初始化中包含之尾端逗號的處理方式不同。