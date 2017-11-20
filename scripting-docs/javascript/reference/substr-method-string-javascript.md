---
title: "substr 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>substr 方法 (字串) (JavaScript)
取得子字串開始的指定位置，以及取得指定的長度。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>參數  
 `stringvar`  
 必要項。 字串常值或`String`物件擷取子字串。  
  
 `start`  
 必要項。 所需的子字串開始位置。 在字串中的第一個字元的索引為零。  
  
 `length`  
 選擇項。 要傳回的子字串中包含的字元數。  
  
## <a name="remarks"></a>備註  
 如果`length`為零或負數，空字串會傳回。 如果未指定，子字串會繼續結尾`stringvar`。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `substr` 方法。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [substring 方法 (String)](../../javascript/reference/substring-method-string-javascript.md)