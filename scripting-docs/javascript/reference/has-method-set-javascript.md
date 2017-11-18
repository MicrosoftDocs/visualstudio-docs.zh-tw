---
title: "has 方法 (Set) (JavaScript) |Microsoft 文件"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-set-javascript"></a>has 方法 (Set) (JavaScript)
傳回`true`如果集合包含指定的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>參數  
 `setObj`  
 必要項。 `Set` 物件。  
  
 `value`  
 必要項。 要測試的項目。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 如果集合包含指定的項目，則為 `true`。  
  
## <a name="example"></a>範例  
 下列範例示範如何將成員加入 `Set`，然後檢查集合是否包含特定成員。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]