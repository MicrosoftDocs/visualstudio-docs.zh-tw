---
title: add 方法 (WeakSet) (JavaScript) |Microsoft 文件
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632828"
---
# <a name="add-method-weakset-javascript"></a>add 方法 (WeakSet) (JavaScript)
將新項目加入 `WeakSet`。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>參數  
 `weaksetObj`  
 必要項。 `WeakSet` 物件。  
  
 `obj`  
 必要項。 `WeakSet` 的新項目。  
  
## <a name="remarks"></a>備註  
 新項目必須是物件 (而不是任意值)，而且必須是唯一的。 如果您將非唯一的項目加入至 `WeakSet`，新項目不會加入至集合 (Collection)。  
  
## <a name="example"></a>範例  
 下列範例示範如何將成員加入集合，然後檢查是否已加入這些成員。  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]