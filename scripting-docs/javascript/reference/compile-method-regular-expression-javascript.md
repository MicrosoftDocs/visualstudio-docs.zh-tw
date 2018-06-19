---
title: compile 方法 （規則運算式） 的 (JavaScript) |Microsoft 文件
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
- compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634248"
---
# <a name="compile-method-regular-expression-javascript"></a>compile 方法 (規則運算式) (JavaScript)
規則運算式編譯成內部格式，加快執行速度。  
  
## <a name="syntax"></a>語法  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>參數  
 `rgExp`  
 必要項。 執行個體**規則運算式**物件。 可以是變數名稱或常值。  
  
 *模式*  
 必要項。 包含要編譯規則運算式模式的字串運算式  
  
 `flags`  
 選擇項。 可用的旗標 (可能已合併) 如下：  
  
-   g (全域搜尋所有出現的*模式*)  
  
-   i (忽略大小寫)  
  
-   m (多行搜尋)  
  
## <a name="remarks"></a>備註  
 **編譯**方法轉換*模式*成內部格式，加快執行速度。 這樣可以更有效率地使用規則運算式在迴圈中，例如。 已編譯的規則運算式會加快項目重複重複使用相同的運算式。 不取得任何優點，不過，如果規則運算式變更時。  
  
## <a name="example"></a>範例  
 下列範例說明使用**編譯**方法：  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**:[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式語法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)