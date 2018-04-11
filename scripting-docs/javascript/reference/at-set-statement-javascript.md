---
title: '@set 陳述式 (JavaScript) |Microsoft 文件'
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
- '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="set-statement-javascript"></a>@set 陳述式 (JavaScript)
建立用於條件式編譯陳述式的變數。  
  
> [!WARNING]
>  Internet Explorer 11 標準模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援條件式編譯。 Internet Explorer 10 標準模式 (含) 以前的所有版本都支援條件式編譯。  
  
## <a name="syntax"></a>語法  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>參數  
 *varname*  
 必要。 有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 變數名稱。 任何時候前面都必須有一個 "@" 字元。  
  
 `term`  
 必要。 零或多個一元運算子，後面接著一個常數、條件式編譯變數或括號運算式。  
  
## <a name="remarks"></a>備註  
 條件式編譯可支援數值和布林變數， 但不支援字串。 使用 `@set` 建立的變數通常用於條件式編譯陳述式，但是也可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼中的任何位置使用。  
  
 以下為變數宣告的範例：  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 括號運算式中支援下列運算子：  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 如果在定義變數之前使用該變數，則其值為 `NaN`。 您可以使用 `NaN` 陳述式檢查變數值是否為 `@if`：  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 上述程式碼不會有問題，因為 `NaN` 是唯一不等於自己的值。  
  
## <a name="requirements"></a>需求  
 所有 Internet Explorer 版本都支援，但是 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援。  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on 陳述式](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if 陳述式](../../javascript/reference/at-if-statement-javascript.md)