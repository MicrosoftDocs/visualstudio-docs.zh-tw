---
title: 函式沒有有效的原型物件 |Microsoft Docs
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
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817355"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>函式沒有有效的原型物件
您嘗試使用**instanceof**來判斷物件是否衍生自特定的函式類別，但您已將物件的屬性重新定義 `prototype` 為 `null` 或外部物件類型（兩者都不是有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件）。 外部物件可以是主機物件模型中的物件（例如，Internet Explorer 的檔或視窗物件），或是外部 COM 物件。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定函式的 `prototype` 屬性參考有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件。  
  
## <a name="see-also"></a>另請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)