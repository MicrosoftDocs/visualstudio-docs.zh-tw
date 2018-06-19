---
title: substring 方法 （字串） (JavaScript) |Microsoft 文件
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
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640928"
---
# <a name="substring-method-string-javascript"></a>substring 方法 (字串) (JavaScript)
傳回子字串內的指定位置`String`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>參數  
 `start`  
 必要項。 以零為起始的索引的整數，表示子字串的開頭。  
  
 `end`  
 選擇項。 以零為起始的索引的整數，表示子字串的結尾。 子字串中包含的字元最多至但不是包括字元由`end`。  
  
 如果`end`省略，將字元從`start`傳回透過原始字串的結尾。  
  
## <a name="remarks"></a>備註  
 `substring`方法會傳回字串，包含從子字串`start`最多，但不是包括`end`。  
  
 **Substring**方法會使用較低的值`start`和`end`做為子字串的開始點。 例如，strvar.substring (0、 3 **)** 和 strvar.substring （3，0） 傳回相同的子字串。  
  
 如果有任一個`start`或`end`是`NaN`或負值，則會取代為零。  
  
 子字串的長度等於之間差異的絕對值`start`和`end`。 例如，strvar.substring （0，3） 中會傳回子字串的長度和 strvar.substring （3，0） 是三個。  
  
## <a name="example"></a>範例  
 下列範例說明使用**substring**方法。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [substr 方法 (String)](../../javascript/reference/substr-method-string-javascript.md)