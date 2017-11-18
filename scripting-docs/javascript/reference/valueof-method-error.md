---
title: "valueOf 方法 （錯誤） |Microsoft 文件"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7593937530469142265f8081bf3472fa4935aee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-error"></a>valueOf 方法 (錯誤)
傳回錯誤的字串值。  
  
## <a name="syntax"></a>語法  
  
```  
  
error.valueOf()  
```  
  
#### <a name="parameters"></a>參數  
 `error`物件是錯誤的任何執行個體。  
  
## <a name="return-value"></a>傳回值  
 字串 「 錯誤:"再加上的錯誤訊息。  
  
## <a name="example"></a>範例  
 下列範例說明使用`valueOF`日期的方法。  
  
```JavaScript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]