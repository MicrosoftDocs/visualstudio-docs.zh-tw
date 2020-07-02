---
title: 陣列長度必須被指派有限的正數 |Microsoft Docs
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
ms.openlocfilehash: 30e02f4f90300e2c05076553419cda5f8c353ab0
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817680"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>陣列長度必須被指派為有限的正值
設定現有**陣列**物件的**length**屬性時，您指定的陣列長度不是正數或零。 當您將值指派給**length** `Array` 負或不是數位（）之物件的 length 屬性時，就會發生這個錯誤 `NaN` 。 請注意， [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會自動將小數位數轉換成整數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將正整數指派給 length 屬性。 陣列的大小沒有上限，而不是最大整數值（大約4000000000）。 下列範例示範設定**陣列**物件之**length**屬性的正確方式。  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)