---
title: 預期的日期物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572894"
---
# <a name="date-object-expected"></a>必須是日期物件
您嘗試在 `Date` 以外之類型的物件上，叫用**valueOf**方法的**資料**。 這種調用類型的物件必須是 `Date` 的類型。 例如:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只會在 `Date`**類型的物件**上叫用**valueOf**方法。  
  
## <a name="see-also"></a>請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [GetDate 方法（Date）](../../javascript/reference/getdate-method-date-javascript.md)    
 [內建物件](../../javascript/intrinsic-objects-javascript.md)