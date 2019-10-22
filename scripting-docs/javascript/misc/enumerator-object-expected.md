---
title: 必須是列舉值物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572874"
---
# <a name="enumerator-object-expected"></a>必須是列舉值物件
您嘗試在 `Enumerator` 以外之類型的物件上叫用**atEnd、列舉**值、MoveFirst 或列舉值，或枚舉器. **moveNext**方法。 這種調用類型的物件必須是 `Enumerator` 的類型。 以下是違反此規則的程式碼範例：  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只會在 `Enumerator` 類型的物件上叫用**atEnd**、**列舉**值、 **MoveFirst**或列舉值. **moveNext**方法。 若要找出您的物件是否為 `Enumerator` 物件，請使用：  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>請參閱  
 [Enumerator 物件](../../javascript/reference/enumerator-object-javascript.md)