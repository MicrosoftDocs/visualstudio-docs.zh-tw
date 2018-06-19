---
title: delete 方法 (Map) (JavaScript) |Microsoft 文件
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5185b883cf603acdc91fe1f1c833d337c4468ba4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636178"
---
# <a name="delete-method-map-javascript"></a>delete 方法 (Map) (JavaScript)
從對應中移除指定的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
mapObj.delete(key)  
```  
  
#### <a name="parameters"></a>參數  
 `mapObj`  
 必要項。 `Map` 物件。  
  
 `key`  
 必要項。 要移除的項目索引鍵。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 如果已移除項目，則為 `true`。  
  
## <a name="example"></a>範例  
 下列範例示範如何將成員加入`Map`，然後再刪除其中一個。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]