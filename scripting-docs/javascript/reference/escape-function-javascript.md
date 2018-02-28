---
title: "escape 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>escape 函式 (JavaScript)
將字串編碼以讓他們可以讀取所有電腦上。 已取代。  
  
## <a name="syntax"></a>語法  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>備註  
 所需`charString`引數可以是任何`String`物件或要編碼的常值。  
  
 **逸出**函式會傳回字串值 （以 Unicode 格式），其中包含的內容`charstring`。 全部為空格、 標點符號、 重音的字元，而且其他任何非 ASCII 字元會取代`%` *xx*編碼，其中*xx*相當的十六進位數字，代表字元。 例如，空格會傳回為"%20"。  
  
 包含值大於 255 使用儲存的字元**%u** *xxxx*格式。  
  
> [!NOTE]
>  **逸出**函式不應該用來編碼統一資源識別項 (URI)。 使用`encodeURI`和`encodeURIComponent`改為函式。  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函式](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)   
 [unescape 函式](../../javascript/reference/unescape-function-javascript.md)