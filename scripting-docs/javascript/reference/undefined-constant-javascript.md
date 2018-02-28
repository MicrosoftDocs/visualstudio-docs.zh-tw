---
title: "undefined 常數 (JavaScript) |Microsoft 文件"
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
- undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>undefined 常數 (JavaScript)
永遠不會定義，例如未初始化的變數值。  
  
## <a name="syntax"></a>語法  
  
```  
undefined  
```  
  
## <a name="remarks"></a>備註  
 `undefined`常數是屬於`Global`物件，並初始化指令碼引擎時變成可用。 當已宣告但未初始化的變數時，其值會是**未定義**。  
  
 如果尚未宣告變數，您無法比較以`undefined`，但您可以比較的字串"undefined"變數的型別。  
  
 `undefined`常數有用時，會明確地測試，或將變數設定為未定義。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`undefined`常數。  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>需求  
 `undefined`屬性在引進[!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]，且已進行唯讀[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]。  
  
 **適用於**:[全域物件](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [typeof 運算子](../../javascript/reference/typeof-operator-decrementjavascript.md)