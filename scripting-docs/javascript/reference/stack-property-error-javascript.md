---
title: "stack 屬性 （錯誤） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="stack-property-error-javascript"></a>stack 屬性 (錯誤) (JavaScript)
取得或設定字串形式的錯誤堆疊，其中包含堆疊追蹤框架。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>備註  
 建構錯誤時，`stack` 屬性設定為 `undefined`，並在發生錯誤時取得追蹤資訊。 如果多次發生錯誤，則每次發生錯誤時都會更新 `stack` 屬性。  
  
 堆疊框架會顯示以下列格式： **at FunctionName (\<完整限定名稱/URL >:\<行號 >:\<欄號 >)**  
  
 如果您建立自己的 Error 物件，並將堆疊追蹤設定為值，則擲回錯誤時不會覆寫值。  
  
 `stack` 屬性不會在其框架中顯示內嵌函式。 它只會顯示實體堆疊。  
  
## <a name="example"></a>範例  
 下列範例示範如何在攔截到錯誤時取得堆疊。  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何設定堆疊，以及之後如何取得堆疊。  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **適用於**:[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [description 屬性 （錯誤）](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 （錯誤）](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 （錯誤）](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit 屬性 (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)