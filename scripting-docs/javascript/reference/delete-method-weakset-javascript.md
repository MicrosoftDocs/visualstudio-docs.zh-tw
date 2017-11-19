---
title: "delete 方法 (WeakSet) (JavaScript) |Microsoft 文件"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46eeac8ddd0072712c1867bc2a419a4e3255ffd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-weakset-javascript"></a>delete 方法 (WeakSet) (JavaScript)
將指定的項目從 `WeakSet` 中移除。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
weaksetObj.delete(obj)  
```  
  
#### <a name="parameters"></a>參數  
 `weaksetObj`  
 必要項。 `WeakSet` 物件。  
  
 `obj`  
 必要項。 要移除的項目。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 如果已移除項目，則為 `true`。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入和刪除 `WeakSet` 的項目。  
  
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