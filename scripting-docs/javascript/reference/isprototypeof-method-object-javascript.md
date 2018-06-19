---
title: isPrototypeOf 方法 (Object) (JavaScript) |Microsoft 文件
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
- isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637378"
---
# <a name="isprototypeof-method-object-javascript"></a>isPrototypeOf 方法 (Object) (JavaScript)
判斷某個物件是否存在於另一個物件的原型鏈結中。  
  
## <a name="syntax"></a>語法  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>參數  
 `prototype`  
 必要項。 物件原型。  
  
 `object`  
 必要項。 將檢查其原型鏈結的另一個物件。  
  
## <a name="remarks"></a>備註  
 如果 `isPrototypeOf` 的原型鏈結中有 `true`，則 `object` 方法會傳回 `prototype`。 原型鏈結可用來在同一種物件類型的執行個體之間共用功能。 當 `isPrototypeOf` 不是物件或是 `false` 沒有出現在 `object` 的原型鏈結中時，`prototype` 方法會傳回 `object`。  
  
## <a name="example"></a>範例  
 在下列程式碼中，說明了如何使用 `isPrototypeOf` 方法。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [prototype 屬性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)