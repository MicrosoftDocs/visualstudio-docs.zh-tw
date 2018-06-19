---
title: Math.log 函式 (JavaScript) |Microsoft 文件
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
- log
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- log method
- Math object
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62bfb6bf9bb95b541a51224af4484ded22ccb4e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638908"
---
# <a name="mathlog-function-javascript"></a>Math.log 函式 (JavaScript)
傳回自然對數 (基底`e`) 數字。  
  
## <a name="syntax"></a>語法  
  
```  
Math.log(number)   
```  
  
#### <a name="parameters"></a>參數  
 數字  
 數字。  
  
## <a name="return-value"></a>傳回值  
 如果`number`是正數，此函數會傳回數字的自然對數。 如果`number`是負數，此函數會傳回`NaN`。 如果`number`為 0，此函數會傳回`-Infinity`。  
  
## <a name="example"></a>範例  
 下列程式碼會示範如何使用這個函式。  
  
```JavaScript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [Math.sqrt 函式](../../javascript/reference/math-sqrt-function-javascript.md)