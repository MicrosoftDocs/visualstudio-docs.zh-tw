---
description: 您嘗試在枚舉器以外的類型物件上叫用 atEnd、列舉值、moveFirst 或列舉值。 moveNext 方法是在列舉值以外的物件上叫用。
title: 預期的列舉值物件 |Microsoft 檔
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
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571047"
---
# <a name="enumerator-object-expected"></a>必須是列舉值物件
您嘗試在以外的類型物件上叫用 **atEnd、** 列舉值、MoveFirst 或列舉值。 **moveNext** 方法的方法是，而不是 `Enumerator` 。 這種調用類型的物件必須是型別 `Enumerator` 。 以下是中斷此規則的程式碼範例：  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請只叫用類型之物件上的 **列舉值 atEnd**、 **列舉** 值、 **moveFirst** 或 **枚舉** 器 `Enumerator` 方法。 若要找出您的物件是否為 `Enumerator` 物件，請使用：  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Enumerator 物件](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)
