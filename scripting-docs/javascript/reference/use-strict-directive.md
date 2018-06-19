---
title: use strict 指示詞 |Microsoft 文件
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
- strict_JavaScriptKeyword
- use strict
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict directive
- use strict
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd951255f5d5719c3aa216965605840ba12010d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640418"
---
# <a name="use-strict-directive"></a>use strict 指示詞
限制某些功能在 JavaScript 中的使用。 在 Internet Explorer 10 中支援和[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]僅限應用程式。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
use strict  
```  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列程式碼會造成語法錯誤，因為在 strict 模式中所有的變數必須宣告與`var`。  
  
```JavaScript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [Strict Mode](../../javascript/advanced/strict-mode-javascript.md)