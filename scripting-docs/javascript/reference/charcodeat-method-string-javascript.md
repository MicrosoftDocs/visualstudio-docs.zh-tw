---
title: charCodeAt 方法 （字串） (JavaScript) |Microsoft 文件
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
- charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633948"
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt 方法 (字串) (JavaScript)
傳回指定之位置處的字元的 Unicode 值。  
  
## <a name="syntax"></a>語法  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>參數  
 `strObj`  
 必要項。 任何`String`物件或字串常值。  
  
 `index`  
 必要項。 所需字元以零為起始的索引。 如果指定的索引處的字元`NaN`傳回。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `charCodeAt` 方法。  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [String.fromCharCode 函式](../../javascript/reference/string-fromcharcode-function-javascript.md)