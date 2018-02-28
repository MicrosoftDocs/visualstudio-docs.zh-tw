---
title: "isFinite 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isfinite-function-javascript"></a>isFinite 函式 (JavaScript)
判斷所提供的數值是否有限。  
  
## <a name="syntax"></a>語法  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>備註  
 所需`number`引數是數字的任何值。  
  
 `isFinite`函式會傳回`true`如果`number`以外是任何值`NaN`、 無限大的負數或正的無限大。 在這三種情況下，它會傳回**false**。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)