---
title: startsWith 方法 （字串） (JavaScript) |Microsoft 文件
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74970a9a3bfe280e91f2df39340732eda8664142
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640138"
---
# <a name="startswith-method-string-javascript"></a>startsWith 方法 (字串) (JavaScript)
傳回值，指出字串或子字串的開頭是否為另一個指定的字串。  
  
## <a name="syntax"></a>語法  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 要搜尋的字串物件。  
  
 `str`  
 必要項。 搜尋字串。  
  
 `position`  
 選擇項。 字串物件中要搜尋的第一個字元位置，從 0 開始。  
  
## <a name="return-value"></a>傳回值  
 如果開頭為 `position` 的字串開始於搜尋字串，則 `startsWith` 方法會傳回 `true`否則傳回 `false`。  
  
## <a name="exceptions"></a>例外狀況  
 如果 `str` 是 `RegExp`，則會擲回 `TypeError`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]