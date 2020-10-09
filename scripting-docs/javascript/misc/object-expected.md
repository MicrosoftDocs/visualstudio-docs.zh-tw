---
title: 預期的物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862113"
---
# <a name="object-expected"></a>必須是物件
您嘗試對非 `Object` 類型的物件叫用方法或屬性，或在需要 `Object` 時傳遞非 `Object` 類型的引數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只能對 `Object` 類型的物件叫用方法或屬性。  
  
- 如果非物件引數發生錯誤，請傳遞 `Object` 類型的物件。  
  
- 確認是否叫用未定義或 Null 參考，而非 `Object` 類型的物件。  
  
     例如，如果您針對下列程式碼中的 myVar 收到這個錯誤：  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     您可以改用此程式碼：  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>請參閱  
 [Object 物件](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [物件和陣列](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)