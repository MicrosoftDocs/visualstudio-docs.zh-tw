---
title: "trim 方法 （字串） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>trim 方法 (字串) (JavaScript)
移除字串前後的空白字元以及行結束字元。  
  
## <a name="syntax"></a>語法  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>參數  
 `stringObj`  
 必要項。 `String` 物件或字串常值。 `trim` 方法不會修改這個字串。  
  
## <a name="return-value"></a>傳回值  
 包含前後空白字元及行結束字元的原始字串已移除。  
  
## <a name="remarks"></a>備註  
 移除的字元包括空格、定位字元、換頁字元、歸位字元和換行字元。 請參閱[特殊字元](../../javascript/advanced/special-characters-javascript.md)的空白字元以及行結束字元的字元的完整清單。  
  
 如需示範如何實作您自己的修剪方法的範例，請參閱[原型和原型繼承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `trim` 方法。  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [特殊字元](../../javascript/advanced/special-characters-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)   
 [捲動、 移動和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)