---
title: 必須是規則運算式物件 |Microsoft 文件
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a5a0f3cb3b86e2e01d522f85d0dae23e9c9d3ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632778"
---
# <a name="regular-expression-object-expected"></a>必須是規則運算式物件
您嘗試叫用**RegExp.prototype.toString**或**RegExp.prototype.valueOf**方法以外的類型的物件上`RegExp`。 這種類型的引動過程的物件必須屬於型別`RegExp`。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只能叫用**RegExp.prototype.toString**或**RegExp.prototype.valueOf**類型的物件上的方法`RegExp`。  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)