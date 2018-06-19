---
title: constructor 屬性 （日期） |Microsoft 文件
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798064117e17ee5b2988396de3c6545917373b10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636098"
---
# <a name="constructor-property-date"></a>constructor 屬性 (日期)
指定的函式，建立日期。  
  
## <a name="syntax"></a>語法  
  
```  
  
date.constructor  
```  
  
## <a name="remarks"></a>備註  
 所需`date`是日期物件的名稱。  
  
 `constructor` 屬性是具有原型之每個物件的原型成員。 `constructor` 屬性包含用來建構該特定物件執行個體的函式參考。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用建構函式屬性。  
  
```JavaScript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]