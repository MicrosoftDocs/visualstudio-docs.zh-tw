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
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064865"
---
# <a name="enumerator-object-expected"></a>必須是列舉值物件
您嘗試叫用**Enumerator.prototype.atEnd、 Enumerator.prototype.moveFirst，Enumerator.prototype.item**或**Enumerator.prototype.moveNext**其他類型的物件上的方法比`Enumerator`。 這種類型的引動過程的物件必須是型別`Enumerator`。 以下是違反此規則的程式碼範例：  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只能叫用**Enumerator.prototype.atEnd**， **Enumerator.prototype.item**， **Enumerator.prototype.moveFirst**，或**Enumerator.prototype.moveNext**類型的物件上的方法`Enumerator`。 若要查看您的物件是否為`Enumerator`物件，請使用：  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Enumerator 物件](../../javascript/reference/enumerator-object-javascript.md)