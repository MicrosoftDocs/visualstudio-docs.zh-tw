---
title: Symbol.for 函式 (JavaScript) |Microsoft 文件
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639658"
---
# <a name="symbolfor-function-javascript"></a>Symbol.for 函式 (JavaScript)
傳回指定索引鍵的符號；如果索引鍵不存在，則使用新的索引鍵建立新的符號物件。  
  
## <a name="syntax"></a>語法  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>參數  
 `key`  
 必要項。 符號的索引鍵，也可做為描述。  
  
## <a name="remarks"></a>備註  
 這個方法會搜尋全域符號登錄中的符號。 如果您將符號序列化為字串，請使用全域符號登錄，以確定特定字串在所有查閱中都會對應到正確符號。  
  
## <a name="example"></a>範例  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]