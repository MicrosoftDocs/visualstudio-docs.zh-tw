---
title: eval 函式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636438"
---
# <a name="eval-function-javascript"></a>eval 函式 (JavaScript)
評估[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼，並加以執行。  
  
## <a name="syntax"></a>語法  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>參數  
 `codeString`  
 必要項。 A`String`包含有效的值[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程式碼。  
  
## <a name="remarks"></a>備註  
 `eval`函式會啟用動態執行[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]原始程式碼。  
  
 `codeString`剖析字串[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]剖析器和執行。  
  
 程式碼傳遞給`eval`函式在呼叫相同的內容中執行`eval`函式。  
  
 您應該盡可能使用[JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)還原序列化的 JavaScript Object Notation (JSON) 的文字。 `JSON.parse`函式更安全，並執行速度比`eval`函式。  
  
## <a name="example"></a>範例  
 下列程式碼將變數初始化`myDate`測試日期。  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)