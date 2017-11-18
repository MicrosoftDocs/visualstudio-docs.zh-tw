---
title: "atEnd 方法 （列舉程式） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: atEnd
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: atEnd method
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b5097d00c11ffafc314264f134aedda3981c8e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="atend-method-enumerator-javascript"></a>atEnd 方法 (列舉程式) (JavaScript)
傳回布林值，指出列舉值是否位於集合的結尾。  
  
> [!WARNING]
>  僅 Internet Explorer 才支援此物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
myEnum.atEnd()  
```  
  
## <a name="remarks"></a>備註  
 必要的 *myEnum* 參考為任何 `Enumerator` 物件。  
  
 如果目前的項目是集合中的最後一個項目、集合為空或目前的項目未定義， `atEnd` 方法就會傳回 **true** 。 否則會傳回 **false**。  
  
## <a name="example"></a>範例  
 在下列程式碼中，使用 `atEnd` 方法來確定是否已到達磁碟機清單的結尾：  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
 **適用於**： [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [item 方法 （列舉程式）](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst 方法 （列舉程式）](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext 方法 （列舉程式）](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Enumerator 物件](../../javascript/reference/enumerator-object-javascript.md)