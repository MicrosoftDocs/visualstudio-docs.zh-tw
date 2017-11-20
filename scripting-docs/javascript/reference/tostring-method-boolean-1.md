---
title: "toString 方法 （布林值） 1 |Microsoft 文件"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-boolean-1"></a>toString 方法 （布林值） 1
傳回物件的字串表示。  
  
## <a name="syntax"></a>語法  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>參數  
 `boolean`  
 必要項。 要取得的字串表示的物件。  
  
## <a name="return-value"></a>傳回值  
 如果布林值為`true`，傳回"true"。 反之則傳回"false"。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例說明使用**toString**方法。  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]