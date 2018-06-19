---
title: Object.getOwnPropertySymbols 函式 (JavaScript) |Microsoft 文件
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cc47ae365841332f11cb02da1469a4c9fff80c3
ms.sourcegitcommit: abae48f476832f79cc2c5bac43bb1226d3fe4e48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2018
ms.locfileid: "27814956"
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols 函式 (JavaScript)
傳回物件的擁有符號屬性。 物件的擁有符號屬性直接定義於該物件上，而且不是繼承自物件的原型。  
  
## <a name="syntax"></a>語法  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>參數  
 `object`  
 必要。 包含擁有符號的物件。  
  
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
  
console.log(symbols[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]