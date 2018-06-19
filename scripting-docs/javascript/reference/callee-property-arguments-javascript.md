---
title: callee 屬性 (arguments) (JavaScript) |Microsoft 文件
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
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634058"
---
# <a name="callee-property-arguments-javascript"></a>callee 屬性 (引數) (JavaScript)
傳回`Function`物件正在執行，也就是指定的本文`Function`物件。  
  
## <a name="syntax"></a>語法  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>備註  
 選擇性*函式*引數是目前執行中的名稱`Function`物件。  
  
 `callee`屬性所屬的**引數**可用只有當關聯的函式正在執行的物件。  
  
 初始值`callee`屬性是`Function`物件正在執行。 這可讓匿名函式是遞迴。  
  
## <a name="example"></a>範例  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用對象**:[引數物件](../../javascript/reference/arguments-object-javascript.md)&#124;[函式物件](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [caller 屬性 (Function)](../../javascript/reference/caller-property-function-javascript.md)