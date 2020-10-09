---
title: 預期的列舉值物件 |Microsoft Docs
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
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862637"
---
# <a name="enumerator-object-expected"></a>必須是列舉值物件
您嘗試在以外的類型物件上叫用 **atEnd、** 列舉值、MoveFirst 或列舉值。 **moveNext** 方法的方法是，而不是 `Enumerator` 。 這種調用類型的物件必須是型別 `Enumerator` 。 以下是中斷此規則的程式碼範例：  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請只叫用類型之物件上的 **列舉值 atEnd**、 **列舉**值、 **moveFirst**或 **枚舉** 器 `Enumerator` 方法。 若要找出您的物件是否為 `Enumerator` 物件，請使用：  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>請參閱  
 [Enumerator 物件](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)