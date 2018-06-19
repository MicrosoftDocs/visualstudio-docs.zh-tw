---
title: delete 方法 (Set) (JavaScript) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636088"
---
# <a name="delete-method-set-javascript"></a>delete 方法 (Set) (JavaScript)
從集合移除指定的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>參數  
 `setObj`  
 必要項。 `Set` 物件。  
  
 `value`  
 必要項。 要移除的項目。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 如果已移除項目，則為 `true`。  
  
## <a name="example"></a>範例  
 下列範例示範如何將成員加入`Set`，然後再刪除其中一個。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]