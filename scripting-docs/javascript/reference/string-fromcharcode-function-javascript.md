---
title: String.fromCharCode 函式 (JavaScript) |Microsoft 文件
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
- fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639838"
---
# <a name="stringfromcharcode-function-javascript"></a>String.fromCharCode 函式 (JavaScript)
從一些 Unicode 字元值中傳回字串。  
  
## <a name="syntax"></a>語法  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>參數  
 `String`  
 必要項。 `String` 物件。  
  
 `code1`, . 。 。 , `codeN`  
 選擇項。 一系列的 Unicode 字元值轉換為字串。 如果任何引數不提供，結果會是空的字串。  
  
## <a name="remarks"></a>備註  
 您可以呼叫此函式上`String`物件而不是在字串執行個體上。  
  
 下列範例會示範如何使用這個方法：  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [charCodeAt 方法 (String)](../../javascript/reference/charcodeat-method-string-javascript.md)