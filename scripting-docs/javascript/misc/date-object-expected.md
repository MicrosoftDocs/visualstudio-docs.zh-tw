---
title: 必須是日期物件 |Microsoft Docs
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
ms.openlocfilehash: a53ff758622cf719c2b10ea47fc516ac8684eb6a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842243"
---
# <a name="date-object-expected"></a>必須是日期物件
您嘗試叫用**Date.prototype.toString**或是**Date.prototype.valueOf**以外的類型的物件上的方法`Date`。 這種類型的引動過程的物件必須是型別`Date`。 例如:   
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只能叫用**Date.prototype.toString**或是**Date.prototype.valueOf**類型的物件上的方法`Date`。  
  
## <a name="see-also"></a>另請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法 （日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [內建物件](../../javascript/intrinsic-objects-javascript.md)