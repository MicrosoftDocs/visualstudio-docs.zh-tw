---
title: 陣列長度必須是有限的正整數 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0b827e0cef5cd6c6ea4aeaddc9f32f02004c214
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862207"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>陣列長度必須是有限的正整數
您使用不是整數的引數來呼叫 **陣列** 的函式， (整數包含零，再加上一組正整數) 。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只有在建立新的物件時，才使用正整數 `Array` 。 如果您想要使用不是整數的單一元素來建立陣列，請在兩個步驟的程式中執行。 首先，建立具有一個元素的陣列，然後將值放在第一個元素 (陣列 [0] ) 。 以下是產生此錯誤的範例。  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     下列範例示範如何使用單一數值元素來指定陣列的正確方式。  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     陣列的大小沒有上限，除了最大整數值 (大約 4000000000) 。  
  
## <a name="see-also"></a>請參閱  
 [使用陣列](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)