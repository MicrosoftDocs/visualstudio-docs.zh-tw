---
title: valueOf 方法 (Object) (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641628"
---
# <a name="valueof-method-object-javascript"></a>valueOf 方法 (Object) (JavaScript)
傳回指定物件的基本值。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>備註  
 所需`object`參考是任何內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件。  
  
 `valueOf`方法定義不同，每個內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件。  
  
|物件|傳回值|  
|------------|------------------|  
|陣列|傳回陣列的執行個體。|  
|Boolean|布林值。|  
|日期|以毫秒為單位，年 1 月 1，1970年午夜 UTC 儲存的時間值。|  
|函式|函式本身。|  
|數字|數值。|  
|物件|物件本身。 這是預設值。|  
|String|字串值。|  
  
 **數學**和`Error`物件不具有`valueOf`方法。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **適用於**: [Array 物件](../../javascript/reference/array-object-javascript.md)&#124;[Boolean 物件](../../javascript/reference/boolean-object-javascript.md)&#124;[日期物件](../../javascript/reference/date-object-javascript.md)&#124;[函式物件](../../javascript/reference/function-object-javascript.md)&#124;[編號物件](../../javascript/reference/number-object-javascript.md)&#124;[物件物件](../../javascript/reference/object-object-javascript.md)&#124;[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toString 方法 (Object)](../../javascript/reference/tostring-method-object-javascript.md)