---
title: toString 方法 （錯誤） |Microsoft 文件
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640588"
---
# <a name="tostring-method-error"></a>toString 方法 (錯誤)
傳回錯誤的字串表示。  
  
## <a name="syntax"></a>語法  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>參數  
 `date`  
 必要項。 要表示為字串時發生錯誤。  
  
## <a name="return-value"></a>傳回值  
 傳回 「 錯誤:"再加上的錯誤訊息。  
  
## <a name="example"></a>範例  
 下列範例說明使用`toString`錯誤的方法。  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]