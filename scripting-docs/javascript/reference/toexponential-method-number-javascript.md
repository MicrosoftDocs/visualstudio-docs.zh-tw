---
title: toExponential 方法 （數字） (JavaScript) |Microsoft 文件
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
- toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640288"
---
# <a name="toexponential-method-number-javascript"></a>toExponential 方法 (數字) (JavaScript)
代表指數標記法之數字。  
  
## <a name="syntax"></a>語法  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>參數  
 `numObj`  
 必要項。 A**數目**物件。  
  
 `fractionDigits`  
 選擇項。 小數點後數字的數目。 必須在 0-20，（含) 範圍。  
  
## <a name="return-value"></a>傳回值  
 傳回指數標記法中的數字的字串表示。 此字串包含小數點，前面有一個數字，可能會包含`fractionDigits`其後的數字。  
  
 如果`fractionDigits`未提供`toExponential`方法會傳回一樣多的數字必須唯一地指定數字。  
  
## <a name="example"></a>範例  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toFixed 方法 （數字）](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision 方法 (Number)](../../javascript/reference/toprecision-method-number-javascript.md)