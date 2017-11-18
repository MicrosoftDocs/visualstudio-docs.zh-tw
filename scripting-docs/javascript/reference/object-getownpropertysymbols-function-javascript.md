---
title: "Object.getOwnPropertySymbols 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols 函式 (JavaScript)
傳回物件的擁有符號屬性。 物件的擁有符號屬性直接定義於該物件上，而且不是繼承自物件的原型。  
  
## <a name="syntax"></a>語法  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要項。 包含擁有符號的物件。  
  
## <a name="return-value"></a>傳回值  
 包含物件之擁有符號的陣列。  
  
## <a name="remarks"></a>備註  
 您需要使用 `Object.getOwnPropertySymbols` 才能取得物件的符號屬性。 `Object.getOwnPropertyNames` 將不會傳回符號屬性。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何取得物件的符號屬性。  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]