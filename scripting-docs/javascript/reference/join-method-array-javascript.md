---
title: join 方法 （陣列） (JavaScript) |Microsoft 文件
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
- join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637608"
---
# <a name="join-method-array-javascript"></a>join 方法 (陣列) (JavaScript)
加入指定的分隔符號字串所分隔陣列的所有項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 `Array` 物件。  
  
 `separator`  
 選擇項。 字串，用來分隔從產生的下一個元素的陣列`String`。 如果省略，則陣列元素會以逗號分隔。  
  
## <a name="remarks"></a>備註  
 如果陣列的任何項目是**未定義**或`null`，它會被視為空字串。  
  
## <a name="example"></a>範例  
 下列範例說明使用**聯結**方法。  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)