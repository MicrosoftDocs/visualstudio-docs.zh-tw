---
title: Number.isInteger 函式 （數字） (JavaScript) |Microsoft 文件
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638798"
---
# <a name="numberisinteger-function-number-javascript"></a>Number.isInteger 函式 (數字) (JavaScript)
傳回布林值，表示值是否為整數。  
  
## <a name="syntax"></a>語法  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>傳回值  
 如果值是整數，則為 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>範例  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```