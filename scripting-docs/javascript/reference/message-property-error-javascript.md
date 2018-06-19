---
title: message 屬性 （錯誤） (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638568"
---
# <a name="message-property-error-javascript"></a>message 屬性 (錯誤) (JavaScript)
會傳回錯誤訊息字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>參數  
 `errorObj`  
 必要項。 執行個體`Error`物件。  
  
## <a name="remarks"></a>備註  
 `message`屬性會傳回包含與特定的錯誤相關聯的錯誤訊息字串。  
  
 `description`和`message`屬性會提供相同的功能。 `description`屬性提供回溯相容性;`message`屬性符合 ECMA 標準。  
  
## <a name="example"></a>範例  
 下例會 TypeError 擲回例外狀況是，並顯示錯誤和錯誤訊息的名稱。  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>範例  
 此程式碼的輸出如下所示。  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用於**:[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [description 屬性 （錯誤）](../../javascript/reference/description-property-error-javascript.md)   
 [name 屬性 (Error)](../../javascript/reference/name-property-error-javascript.md)