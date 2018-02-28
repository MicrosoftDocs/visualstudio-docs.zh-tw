---
title: "with 陳述式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with 陳述式 (JavaScript)
為一個陳述式建立預設物件。  
  
## <a name="syntax"></a>語法  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>參數  
 `object`  
 預設物件。  
  
 `statements`  
 一個或多個陳述式，`object` 為該陳述式的預設物件。  
  
## <a name="remarks"></a>備註  
 `with` 陳述式通常用來減少您在某些情況下必須撰寫的程式碼數量。  
  
> [!WARNING]
>  在 strict 模式中不允許使用 `with`。 使用 `with` 可能會讓程式碼更難閱讀及偵錯，通常應該避免。  
  
## <a name="example"></a>範例  
 在這個範例中，會重複使用 `Math` 物件：  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>範例  
 如果您將範例重新撰寫為使用 `with` 陳述式，您的程式碼會變得更簡潔：  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [this 陳述式](../../javascript/reference/this-statement-javascript.md)