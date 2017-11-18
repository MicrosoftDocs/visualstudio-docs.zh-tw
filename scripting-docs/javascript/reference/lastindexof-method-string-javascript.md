---
title: "lastIndexOf 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf 方法 (字串) (JavaScript)
傳回字串中的最後一個相符的子字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>參數  
 `strObj`  
 必要項。 `String` 物件或字串常值。  
  
 `substring`  
 必要項。 要搜尋的子字串。  
  
 `startindex`  
 選擇項。 要開始搜尋索引。 如果省略，則會在字串結尾開始搜尋。  
  
## <a name="remarks"></a>備註  
 **LastIndexOf**方法會傳回整數值，指出字串中子字串的開頭`String`物件。 如果找不到子字串，則傳回-1。  
  
 如果 `startindex` 是負數，則會將 `startindex` 視為零。 如果大於最大的字元位置索引，它會被視為最大可能的索引。  
  
 搜尋被由字串中最後一個字元開始。 否則，這個方法相當於**indexOf**。  
  
 下列範例說明使用**lastIndexOf**方法。  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [indexOf 方法 (字串)](../../javascript/reference/indexof-method-string-javascript.md)