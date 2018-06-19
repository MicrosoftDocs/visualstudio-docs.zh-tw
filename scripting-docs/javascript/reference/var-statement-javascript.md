---
title: var 陳述式 (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641358"
---
# <a name="var-statement-javascript"></a>var 陳述式 (JavaScript)
宣告變數。  
  
## <a name="syntax"></a>語法  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>參數  
 `variable1`  
 所宣告的變數名稱。  
  
 `value1`  
 指派給變數的初始值。  
  
## <a name="remarks"></a>備註  
 使用`var`陳述式來宣告變數。 當您宣告的變數，或稍後在您的指令碼中，您可以指派值。  
  
 第一次宣告變數出現在您的指令碼。  
  
 您可以將變數宣告而不使用`var`關鍵字，並將指派給它的值。 這稱為*隱含宣告*，也不建議。 隱含的宣告提供變數的全域範圍。 當您宣告的變數在程序層級時，不過，通常不想它具有全域範圍。 若要避免提供變數的全域範圍，您必須使用`var`變數宣告中的關鍵字。  
  
 如果您未初始化的變數`var`陳述式，它會自動指派[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]值`undefined`。  
  
## <a name="example"></a>範例  
 下列範例說明使用`var`陳述式。  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)   
 [ew 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [變數](../../javascript/variables-javascript.md)