---
title: number 屬性 （錯誤） (JavaScript) |Microsoft 文件
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639098"
---
# <a name="number-property-error-javascript"></a>number 屬性 (錯誤) (JavaScript)
傳回或設定與特定的錯誤相關聯的數值。 `Error`物件的預設屬性是**數目**。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>參數  
 *物件*  
 任何執行個體`Error`物件。  
  
 *錯誤號碼*  
 表示錯誤的整數。  
  
## <a name="remarks"></a>備註  
 錯誤代碼是一個 32 位元的值。 上方的 16 位元字組是設備碼和 facility 為該錯誤碼。 若要判斷錯誤的程式碼，請使用`&`(位元和) 運算子來結合的十六進位數字的數字屬性`0xFFFF`。  
  
## <a name="example"></a>範例  
 下列範例會擲回例外狀況，並顯示錯誤碼，衍生自的錯誤號碼。  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>範例  
 此程式碼的輸出如下所示。  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用於**:[物件時發生錯誤](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [description 屬性 （錯誤）](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 （錯誤）](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 (Error)](../../javascript/reference/name-property-error-javascript.md)