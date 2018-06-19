---
title: constructor 屬性 （數字） |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72679f55aef9b0ac8dc01794c7460dbd8cf0bdf8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636068"
---
# <a name="constructor-property-number"></a>constructor 屬性 (數字)
指定的函式，會建立數字。  
  
## <a name="syntax"></a>語法  
  
```  
  
number.constructor  
```  
  
## <a name="remarks"></a>備註  
 所需`number`是字串的名稱。  
  
 `constructor` 屬性是具有原型之每個物件的原型成員。 這包括所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件除了`Global`和`Math`物件。 `constructor` 屬性包含用來建構該特定物件執行個體的函式參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]