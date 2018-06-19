---
title: concat 方法 （字串） (JavaScript) |Microsoft 文件
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633998"
---
# <a name="concat-method-string-javascript"></a>concat 方法 (字串) (JavaScript)
傳回包含兩個或多個字串串連的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>參數  
 `string1`  
 必要項。 `String`物件或字串常值的所有其他指定，會串連字串。  
  
 `string2,. . ., stringN`  
 選擇項。 要附加至結尾字串`string1`。  
  
## <a name="remarks"></a>備註  
 結果`concat`方法相當於： `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`。 來源或結果字串中的值變更不會影響另一個字串中的值。 如果任何引數不是字串，它們會先轉換成字串串連到之前`string1`。  
  
## <a name="example"></a>範例  
 下列範例說明使用`concat`字串搭配使用時的方法：  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [加法運算子 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)