---
title: codePointAt 方法 （字串） (JavaScript) |Microsoft 文件
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633608"
---
# <a name="codepointat-method-string-javascript"></a>codePointAt 方法 (字串) (JavaScript)
傳回 Unicode UTF-16 字元的字碼指標。  
  
## <a name="syntax"></a>語法  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 字串物件。  
  
 `pos`  
 必要項。 字元的位置。  
  
## <a name="remarks"></a>備註  
 這個方法會傳回所有 UTF-16 字元的字碼指標值，包括星號字碼指標 (具有四個以上十六進位值的字碼指標)。  
  
 如果 `pos` 小於零 (0) 或大於字串的大小，則傳回值為 `undefined`。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `codePointAt` 方法。  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
