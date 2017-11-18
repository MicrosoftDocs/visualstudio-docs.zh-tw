---
title: "Enumerator 物件 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Enumerator 物件 (JavaScript)
啟用集合中項目的列舉。  
  
> [!WARNING]
>  僅 Internet Explorer 才支援此物件， [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式並不予支援。  
  
## <a name="syntax"></a>語法  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>參數  
 `enumObj`  
 必要項。 要對其指派 `Enumerator` 物件的變數名稱。  
  
 `collection`  
 選擇項。 任何 Collection 物件。  
  
## <a name="remarks"></a>備註  
 集合不同於陣列的地方在於無法直接存取集合的成員。 不像您在使用陣列時使用索引，您只能將目前項目指標移至集合的第一個或下一個元素。  
  
 `Enumerator` 物件提供了存取集合之任何成員的方法，類似於 VBScript 中的 `For...Each` 陳述式。  
  
## <a name="example"></a>範例  
 下列程式碼示範 `Enumerator` 物件的用法：  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>屬性  
 `Enumerator` 物件沒有屬性。  
  
## <a name="methods"></a>方法  
 [atEnd 方法](../../javascript/reference/atend-method-enumerator-javascript.md)&#124;[item 方法](../../javascript/reference/item-method-enumerator-javascript.md)&#124;[moveFirst 方法](../../javascript/reference/movefirst-method-enumerator-javascript.md)&#124;[moveNext 方法](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。 請參閱＜ [版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 [Boolean 物件](../../javascript/reference/boolean-object-javascript.md)