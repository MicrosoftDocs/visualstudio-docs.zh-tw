---
title: "indexOf 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>indexOf 方法 (字串) (JavaScript)
傳回子字串第一個出現的位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>參數  
 `strObj`  
 必要項。 A`String`物件或字串常值。  
  
 `subString`  
 必要項。 要在字串中搜尋的子字串  
  
 `startIndex`  
 選擇項。 要開始搜尋 `String` 物件的索引位置。 如果省略，則會從字串的開頭開始搜尋。  
  
## <a name="remarks"></a>備註  
 **IndexOf**方法會傳回中的子字串的開頭`String`物件。 如果找不到子字串，則傳回 -1。  
  
 如果 `startindex` 是負數，則會將 `startindex` 視為零。 如果大於最高的索引，則會將其視為最高的索引。  
  
 搜尋是由左至右進行。 否則，這個方法相當於**lastIndexOf**。  
  
## <a name="example"></a>範例  
 下列範例說明使用**indexOf**方法。  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**:[字串物件](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [lastIndexOf 方法 （字串）](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [捲動、 移動和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)