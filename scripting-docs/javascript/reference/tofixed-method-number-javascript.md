---
title: "toFixed 方法 （數字） (JavaScript) |Microsoft 文件"
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
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>toFixed 方法 (數字) (JavaScript)
代表固定點標記法之數字。  
  
## <a name="syntax"></a>語法  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>參數  
 `numObj`  
 所需的`Number`物件。  
  
 `fractionDigits`  
 選擇項。 小數點後數字的數目。 必須在 0-20，（含) 範圍。  
  
## <a name="return-value"></a>傳回值  
 傳回數字的字串表示以固定點標記法，包含`fractionDigits`小數點後的數字。  
  
 如果`fractionDigits`未提供或**未定義**，預設值為零。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`toFixed`。  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toExponential 方法 （數字）](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision 方法 (Number)](../../javascript/reference/toprecision-method-number-javascript.md)