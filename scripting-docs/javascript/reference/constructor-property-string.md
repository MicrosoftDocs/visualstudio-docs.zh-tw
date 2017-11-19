---
title: "constructor 屬性 （字串） |Microsoft 文件"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-string"></a>constructor 屬性 (字串)
指定的函式，建立字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>備註  
 所需`string`是字串的名稱。  
  
 `constructor` 屬性是具有原型之每個物件的原型成員。 這包括所有內建[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]物件除了`Global`和`Math`物件。 `constructor` 屬性包含用來建構該特定物件執行個體的函式參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]