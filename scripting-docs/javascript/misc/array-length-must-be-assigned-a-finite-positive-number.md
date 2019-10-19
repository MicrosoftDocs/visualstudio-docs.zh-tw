---
title: 陣列長度必須被指派有限的正數 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: cff9c8c42199e106cca5f6f2808866e46a26afe2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576072"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>陣列長度必須被指派為有限的正值
設定現有**陣列**物件的**length**屬性時，您指定的陣列長度不是正數或零。 當您將值指派給負或不是數位（`NaN`） `Array` 物件的**length**屬性時，就會發生這個錯誤。 請注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會自動將小數位數轉換成整數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將正整數指派給 length 屬性。 陣列的大小沒有上限，而不是最大整數值（大約4000000000）。 下列範例示範設定**陣列**物件之**length**屬性的正確方式。  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)