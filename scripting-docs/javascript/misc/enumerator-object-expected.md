---
title: 必須是列舉值物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: ff61894ce808cd33876e876c596e791a3347ab72
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817589"
---
# <a name="enumerator-object-expected"></a>必須是列舉值物件
您嘗試在以外的型別物件上叫用**atEnd、列舉**值、MoveFirst 或列舉值. **moveNext**方法，或執行枚舉器。 `Enumerator` 這種調用類型的物件必須是類型 `Enumerator` 。 以下是違反此規則的程式碼範例：  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只會在類型的物件上叫用**atEnd**、**列舉**值. **MoveFirst**或列舉值. **moveNext** `Enumerator` 方法。 若要找出您的物件是否為 `Enumerator` 物件，請使用：  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Enumerator 物件](../../javascript/reference/enumerator-object-javascript.md)