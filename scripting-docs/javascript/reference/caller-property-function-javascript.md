---
title: "caller 屬性 （函式） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>caller 屬性 (函式) (JavaScript)
取得叫用目前的函式的函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>備註  
 `functionName`物件名稱的任何執行函式。  
  
 `caller`屬性定義的函式只有時，函式正在執行。 如果呼叫此函式會從最上方的層級[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式`caller`包含`null`。  
  
 如果`caller`屬性內容中所用的字串，則結果為相同`functionName`。`toString`，也就是反編譯函式的顯示文字。  
  
 下面範例會說明 `caller` 屬性的使用：  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)