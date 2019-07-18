---
title: 陣列長度必須是有限的正整數 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 31673205a7ca94783985e0249c5664b4bbca6147
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818120"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>陣列長度必須是有限的正整數
您呼叫**陣列**不是整數 （整數包含零，再加上正值的整數的集合） 的引數的建構函式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 只有在建立新時，才使用正整數`Array`物件。 如果您想要建立具有單一元素且不是整數的陣列，則會執行雙步驟程序中。 先建立陣列，含有一個項目，然後將值放在第一個項目 (array[0])。 以下是範例，會產生這個錯誤。  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     下列範例會示範正確的方式來指定陣列與單一數字的項目。  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     最大整數值 （約 4 億） 以外的值陣列的大小沒有上限。  
  
## <a name="see-also"></a>另請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)