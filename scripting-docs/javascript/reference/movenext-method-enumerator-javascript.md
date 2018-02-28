---
title: "moveNext 方法 （列舉程式） (JavaScript) |Microsoft 文件"
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
- moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="movenext-method-enumerator-javascript"></a>moveNext 方法 (列舉程式) (JavaScript)
將目前的項目移至集合中的下一個項目。  
  
> [!WARNING]
>  僅 Internet Explorer 才支援此物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>備註  
 必要的 *enumObj* 參考為任何 `Enumerator` 物件。  
  
 如果列舉值位於集合的結尾或集合是空的，則會將目前的項目設為 undefined。  
  
## <a name="example"></a>範例  
 在下列範例中，使用 **moveNext** 方法來移至 `Drives` 集合中的下一個磁碟機：  
  
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
 [atEnd 方法 （列舉程式）](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [item 方法 （列舉程式）](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst 方法 (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)