---
title: 陣列長度必須被指派為有限的正數 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e0016c7a0a6acb3f08121d8636ccdf848dcf201
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862819"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>陣列長度必須被指派為有限的正值
設定現有**陣列**物件的**length**屬性時，您指定的陣列長度不是正數或零。 當您將值指派給**length** `Array` 負數或非數位 () 的物件長度屬性時，就會發生這個錯誤 `NaN` 。 請注意， [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會自動將小數數位轉換成整數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將正數整數指派給 length 屬性。 陣列的大小沒有上限，除了最大整數值 (大約 4000000000) 。 下列範例將示範設定**陣列**物件之**length**屬性的正確方式。  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>請參閱  
 [使用陣列](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)