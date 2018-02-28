---
title: "必須是日期物件 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-expected"></a>必須是日期物件
您嘗試叫用**Date.prototype.toString**或**Date.prototype.valueOf**方法以外的類型的物件上`Date`。 這種類型的引動過程的物件必須屬於型別`Date`。 例如：  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只能叫用**Date.prototype.toString**或**Date.prototype.valueOf**類型的物件上的方法`Date`。  
  
## <a name="see-also"></a>另請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法 （日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [內建物件](../../javascript/intrinsic-objects-javascript.md)