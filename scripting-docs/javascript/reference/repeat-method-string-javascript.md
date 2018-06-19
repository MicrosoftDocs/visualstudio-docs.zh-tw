---
title: repeat 方法 （字串） (JavaScript) |Microsoft 文件
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638708"
---
# <a name="repeat-method-string-javascript"></a>repeat 方法 (字串) (JavaScript)
傳回新的字串物件，其值等於原始字串重複指定的次數。  
  
## <a name="syntax"></a>語法  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 字串物件。  
  
 `count`  
 必要項。 要在傳回的字串中重複原始字串的次數。  
  
## <a name="exceptions"></a>例外狀況  
 這個方法唯有在引數為負數或 +Infinity 時才會擲回 RangeError。  
  
## <a name="remarks"></a>備註  
 `repeat` 方法會將原始字串串連到新字串，並且多達 `count` 所指定的次數。  
  
 如果 `count` 不是小於 `Infinity` 的正數，這個方法會擲回錯誤。  
  
## <a name="example"></a>範例  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]