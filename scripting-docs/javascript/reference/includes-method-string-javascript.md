---
title: includes 方法 （字串） (JavaScript) |Microsoft 文件
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637028"
---
# <a name="includes-method-string-javascript"></a>includes 方法 (字串) (JavaScript)
傳回布林值，指出字串物件中是否包含傳入的字串。  
  
## <a name="syntax"></a>語法  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 要測試的字串物件。  
  
 `substring`  
 必要項。 要測試的字串。  
  
 `position`  
 選擇項。 字串物件中要測試的第一個字元位置，以 0 開頭。  
  
## <a name="return-value"></a>傳回值  
 如果字串物件中包含傳入的字串，`includes` 方法就會傳回 `true`；否則會傳回 `false`。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]