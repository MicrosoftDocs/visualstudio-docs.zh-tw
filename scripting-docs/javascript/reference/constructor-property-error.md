---
title: "constructor 屬性 （錯誤） |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1ade0ab1ba771b2ff9dfb7051b2983b3da77ed4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-error"></a>constructor 屬性 (錯誤)
指定建立錯誤的函數。  
  
## <a name="syntax"></a>語法  
  
```  
  
error.constructor  
```  
  
## <a name="remarks"></a>備註  
 所需`error`錯誤物件的名稱。  
  
 `constructor` 屬性是具有原型之每個物件的原型成員。 `constructor` 屬性包含用來建構該特定物件執行個體的函式參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]