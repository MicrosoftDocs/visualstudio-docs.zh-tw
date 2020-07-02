---
title: 預期的日期物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817602"
---
# <a name="date-object-expected"></a>必須是日期物件
您嘗試在以外類型的物件上叫用**valueOf** **方法，但**不是 `Date` 。 這種調用類型的物件必須是類型 `Date` 。 例如：  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只會在類型的物件上叫用**valueOf** **方法。** `Date`  
  
## <a name="see-also"></a>另請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法（日期）](../../javascript/reference/getdate-method-date-javascript.md)   
 [內建物件](../../javascript/intrinsic-objects-javascript.md)