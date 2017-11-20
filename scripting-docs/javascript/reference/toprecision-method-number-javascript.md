---
title: "toPrecision 方法 （數字） (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>toPrecision 方法 (數字) (JavaScript)
以指定的數字的數字的指數或固定點標記法中表示數字。  
  
## <a name="syntax"></a>語法  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>參數  
 `numObj`  
 必要項。 `Number` 物件。  
  
 `precision`  
 選擇項。 有效位數的數目。 必須在範圍 1-21，內含。  
  
## <a name="return-value"></a>傳回值  
 指數表示法中的數字`precision`-1 傳回小數點後數字。 固定的標記法中的數字`precision`會傳回有效位數。  
  
 如果`precision`未提供或**未定義**、 **toString**改為呼叫方法。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用`toPrecision`。  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**:[編號物件](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [toFixed 方法 （數字）](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential 方法 (Number)](../../javascript/reference/toexponential-method-number-javascript.md)