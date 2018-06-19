---
title: String.fromCodePoint 函式 (JavaScript) |Microsoft 文件
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
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0905b392606bec9fb59b08a04129ce30cb013db1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639258"
---
# <a name="stringfromcodepoint-function-javascript"></a>String.fromCodePoint 函式 (JavaScript)
傳回與 Unicode UTF-16 字碼指標關聯的字串。  
  
## <a name="syntax"></a>語法  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### <a name="parameters"></a>參數  
 `...codePoints`  
 必要項。 指定一個或多個 UTF-16 字碼指標值的剩餘參數。  
  
## <a name="remarks"></a>備註  
 如果 `...codePoints` 不是有效的 UTF-16 字碼指標，這個函式會擲回 `RangeError` 例外狀況。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `fromCodePoint` 函式。  
  
```JavaScript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]