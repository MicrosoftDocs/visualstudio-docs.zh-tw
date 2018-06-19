---
title: charAt 方法 （字串） (JavaScript) |Microsoft 文件
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
- charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634128"
---
# <a name="charat-method-string-javascript"></a>charAt 方法 (String) (JavaScript)
傳回指定索引中的字元。  
  
## <a name="syntax"></a>語法  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>參數  
 `strObj`  
 必要項。 任何`String`物件或字串常值。  
  
 `index`  
 必要項。 所需字元以零為起始的索引。  
  
## <a name="remarks"></a>備註  
 `charAt`方法會傳回字元值等於指定的字元`index`。 在字串中的第一個字元是在索引 0，第二個位於索引 1，依此類推。 值的`index`所超出範圍傳回空字串。  
  
## <a name="example"></a>範例  
 下列範例說明使用`charAt`方法：  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)