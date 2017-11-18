---
title: "slice 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>slice 方法 (字串) (JavaScript)
傳回字串的一個區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 `String` 物件或字串常值。  
  
 `start`  
 必要項。 開頭的指定部分索引`stringObj`。  
  
 `end`  
 選擇項。 結尾的指定部分索引`stringObj`。 子字串中包含的字元最多至但不是包括字元由`end`。 如果未指定此值，子字串會繼續結尾`stringObj`。  
  
## <a name="remarks"></a>備註  
 `slice`方法會傳回`String`物件，其中包含的指定的部分`stringObj`。  
  
 `slice`方法會複製，但不是包含所指定的字元`end`。  
  
 如果`start`是負數，則會被視為*長度* +  `start`其中*長度*是字串的長度。 如果`end`是負數，則會被視為*長度* + `end`。 如果`end`已省略，則複製會繼續結尾`stringObj`。 如果`end`之前發生`start`，任何字元會複製到新的字串。  
  
## <a name="example"></a>範例  
 在第一個範例中，`slice`方法會傳回整個字串。 在第二個範例中，`slice`方法會傳回整個字串，除了最後一個字元。  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [slice 方法 (陣列)](../../javascript/reference/slice-method-array-javascript.md)