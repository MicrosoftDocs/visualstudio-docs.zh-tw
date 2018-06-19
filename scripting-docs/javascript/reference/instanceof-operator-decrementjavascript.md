---
title: instanceof 運算子 (JavaScript) |Microsoft 文件
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
- instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2124fe815c89c3c157be3ea729fa7edb9d96b39
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
ms.locfileid: "27799575"
---
# <a name="instanceof-operator-javascript"></a>instanceof 運算子 (JavaScript)
傳回的布林值將說明物件是否為某個特定類別的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>參數  
 `result`  
 必要。 任何變數。  
  
 `object`  
 必要。 任何物件運算式。  
  
 `class`  
 必要。 任何定義的物件類別。  
  
## <a name="remarks"></a>備註  
 如果 `instanceof` 是 `true` 的執行個體，`object` 運算子會傳回 `class`。 它會傳回`true`如果`class`存在於物件的原型鏈結中。 如果 `false` 不是 `object` 的執行個體，或者如果 `class` 為 `object`，則會傳回 `null`。  
  
## <a name="example"></a>範例  
 下面範例會示範如何使用 `instanceof` 運算子。  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)