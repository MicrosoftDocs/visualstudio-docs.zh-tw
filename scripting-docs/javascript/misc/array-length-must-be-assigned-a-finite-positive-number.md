---
title: 陣列長度必須被指派有限的正值 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633438"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>陣列長度必須被指派為有限的正值
設定時**長度**屬性的現有**陣列**物件，指定不是正數或零的陣列長度。 當您指派到的值時，會發生這個錯誤**長度**屬性`Array`物件為負數或非數值 (`NaN`)。 請注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]自動將分數轉換成整數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   指派給 length 屬性的正整數。 陣列，最大整數值 （約 10 億 4） 以外的大小沒有上限。 下列範例會示範如何正確設定**長度**屬性**陣列**物件。  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)