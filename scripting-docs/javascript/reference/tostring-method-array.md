---
title: "toString 方法 （陣列） |Microsoft 文件"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-array"></a>toString 方法 (陣列)
傳回陣列的字串表示。  
  
## <a name="syntax"></a>語法  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>參數  
 `array`  
 必要項。 要表示為字串陣列。  
  
## <a name="return-value"></a>傳回值  
 陣列的字串表示。  
  
## <a name="remarks"></a>備註  
 項目`Array`轉換為字串。 產生的字串串連並以逗號分隔。  
  
## <a name="example"></a>範例  
 下列範例說明使用**toString**方法的陣列。  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]