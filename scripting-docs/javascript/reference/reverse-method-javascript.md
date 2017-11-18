---
title: "reverse 方法 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="reverse-method-javascript"></a>reverse 方法 (JavaScript)
中的項目會反轉`Array`。  
  
## <a name="syntax"></a>語法  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>參數  
 `arrayObj`  
 必要項。 任何 `Array` 物件。  
  
## <a name="return-value"></a>傳回值  
 反轉的陣列中。  
  
## <a name="remarks"></a>備註  
 所需`arrayObj`參考是`Array`物件。  
  
 `reverse`方法反轉的項目`Array`就地物件。 它不會建立新`Array`執行期間的物件。  
  
 如果陣列不是連續的`reverse`方法填滿間距的陣列中的陣列中建立項目。 每一種建立項目具有值`undefined`。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `reverse` 方法。  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [concat 方法 (陣列)](../../javascript/reference/concat-method-array-javascript.md)