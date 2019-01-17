---
title: 陣列長度必須是有限的正整數 |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348590"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>陣列長度必須是有限的正整數
您呼叫**陣列**不是整數 （整數包含零，再加上正值的整數的集合） 的引數的建構函式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只有在建立新時，才使用正整數`Array`物件。 如果您想要建立具有單一元素且不是整數的陣列，則會執行雙步驟程序中。 先建立陣列，含有一個項目，然後將值放在第一個項目 (array[0])。 以下是範例，會產生這個錯誤。  
  
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