---
title: 必須是物件 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 09027661b07bbc489dff4985d3858eb8366437a7
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842204"
---
# <a name="object-expected"></a>必須是物件
您嘗試對非 `Object` 類型的物件叫用方法或屬性，或在需要 `Object` 時傳遞非 `Object` 類型的引數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只能對 `Object` 類型的物件叫用方法或屬性。  
  
-   如果非物件引數發生錯誤，請傳遞 `Object` 類型的物件。  
  
-   確認是否叫用未定義或 Null 參考，而非 `Object` 類型的物件。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [Object 物件](../../javascript/reference/object-object-javascript.md)   
 [物件和陣列](../../javascript/objects-and-arrays-javascript.md)