---
title: "unescape 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>unescape 函式 (JavaScript)
將解碼`String`物件經過編碼的`escape`函式。 已取代。  
  
## <a name="syntax"></a>語法  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>備註  
 所需`charString`引數是`String`物件或要解碼的常值。  
  
 `unescape`函式會傳回字串值包含內容的`charstring`。 所有的字元編碼為 %*xx*十六進位格式會取代其 ASCII 字元組對等用法。  
  
 中的字元編碼**%u** *xxxx*格式 （Unicode 字元） 會取代以十六進位編碼的 Unicode 字元*xxxx*。  
  
> [!NOTE]
>  `unescape`函式不應該用來解碼統一資源識別項 (URI)。 使用`decodeURI`和`decodeURIComponent`改為函式。  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape 函式](../../javascript/reference/escape-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)