---
title: toString 方法 （數字） |Microsoft 文件
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6be170061faf4c2782c7247c80c55065c3a6742
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640388"
---
# <a name="tostring-method-number"></a>toString 方法 (數字)
傳回數字的字串表示。  
  
## <a name="syntax"></a>語法  
  
```  
  
number.toString()  
```  
  
## <a name="parameters"></a>參數  
 `number`  
 必要項。 要表示為字串的數字。  
  
## <a name="return-value"></a>傳回值  
 數字的字串表示。  
  
## <a name="example"></a>範例  
 下列範例說明使用**toString**方法以數字。  
  
```JavaScript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]