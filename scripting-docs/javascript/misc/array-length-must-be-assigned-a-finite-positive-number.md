---
title: 陣列長度必須被指派為有限正數 |Microsoft Docs
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
ms.openlocfilehash: 0c6e536047aaebb9bd3a06e38574330937817748
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840788"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>陣列長度必須被指派為有限的正值
設定時**長度**屬性的現有**陣列**物件，指定了不是正數或零的陣列長度。 當您指派的值時，會發生此錯誤**長度**屬性`Array`物件，為負數或不是數字 (`NaN`)。 請注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]自動將小數點後數字轉換成整數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   指派給 length 屬性的正整數。 最大整數值 （約 4 億） 以外的值陣列的大小沒有上限。 下列範例示範設定的正確方式**長度**屬性**陣列**物件。  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)