---
title: 函數沒有有效的原型物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15b00087cd66b873044b7bafb1bfecf4fc91f8d9
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862396"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>函式沒有有效的原型物件
您嘗試使用 **instanceof** 來判斷物件是否衍生自特定的函式類別，但您已將物件的屬性重新定義 `prototype` 為 `null` ，或外部物件類型 (兩個都不是有效 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的物件) 。 外部物件可以是主機物件模型中的物件 (例如 Internet Explorer 的檔或視窗物件) 或外部 COM 物件。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定函式的 `prototype` 屬性參考有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件。  
  
## <a name="see-also"></a>請參閱  
 [Function 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype 屬性 (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)