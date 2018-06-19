---
title: Number.isFinite 函式 （數字） (JavaScript) |Microsoft 文件
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23ff1e80ad71fd9d848f7a0e33628131f5d8014
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638138"
---
# <a name="numberisfinite-function-number-javascript"></a>Number.isFinite 函式 (數字) (JavaScript)
傳回布林值，表示值是否為有限數值。  
  
## <a name="syntax"></a>語法  
  
```  
Number.isFinite(numValue)   
```  
  
## <a name="return-value"></a>傳回值  
 如果值為 `NaN`、`+∞` 或 `-∞`，則為 `false`否則為 `true`。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
  
```JavaScript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)