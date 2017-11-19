---
title: "description 屬性 （錯誤） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>description 屬性 (錯誤) (JavaScript)
傳回或設定與特定的錯誤相關聯的描述性字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>參數  
 *object*  
 必要項。 任何執行個體`Error`物件。  
  
 `stringExpression`  
 選擇項。 包含描述錯誤的字串運算式。  
  
## <a name="remarks"></a>備註  
 **描述**屬性包含與特定的錯誤相關聯的錯誤訊息字串。 使用這個屬性所包含的值來警示使用者已發生錯誤。  
  
 **描述**和**訊息**屬性會提供相同的功能;**描述**屬性提供回溯相容性; **訊息**屬性符合 ECMA 標準。  
  
## <a name="example"></a>範例  
 下列範例說明使用**描述**屬性。  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用於**:[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [number 屬性 （錯誤）](../../javascript/reference/number-property-error-javascript.md)   
 [message 屬性 （錯誤）](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 (Error)](../../javascript/reference/name-property-error-javascript.md)