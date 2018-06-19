---
title: constructor 屬性 （陣列） |Microsoft 文件
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca779a2fa2356c1f3e1ca816f16531c0930459a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633928"
---
# <a name="constructor-property-array"></a>constructor 屬性 (陣列)
指定用來建立陣列的函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
array.constructor  
```  
  
## <a name="remarks"></a>備註  
 所需`array`是陣列的名稱。  
  
 `constructor` 屬性是具有原型之每個物件的原型成員。 這包括所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件除了`Global`和`Math`物件。 `constructor` 屬性包含用來建構該特定物件執行個體的函式參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]