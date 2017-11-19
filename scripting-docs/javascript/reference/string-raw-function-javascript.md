---
title: "String.raw 函式 (JavaScript) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="stringraw-function-javascript"></a>String.raw 函式 (JavaScript)
傳回原始字串形式的範本字串。  
  
## <a name="syntax"></a>語法  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>參數  
 `templateStr`  
 必要項。 樣板字串。  
  
 `obj`  
 必要項。 使用物件常值標記法 (例如 { raw: 'value' }) 指定之語式正確的物件。  
  
 `...substitutions`  
 選擇項。 陣列 ([剩餘參數](../../javascript/functions-javascript.md)) 組成的一或多個替代值。  
  
## <a name="remarks"></a>備註  
 `String.raw`函式適用於搭配[範本字串](../../javascript/advanced/template-strings-javascript.md)。 原始字串將會包含字串中的任何逸出字元和反斜線。  
  
 如果 `obj` 不是語式正確的物件，則會擲回錯誤。  
  
## <a name="example"></a>範例  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]