---
title: has 方法 (Map) (JavaScript) |Microsoft 文件
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636708"
---
# <a name="has-method-map-javascript"></a>has 方法 (Map) (JavaScript)
傳回`true`如果對應包含指定的項目。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>參數  
 `mapObj`  
 必要項。 `Map` 物件。  
  
 `key`  
 必要項。 若要測試的項目索引鍵。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `true`如果對應包含指定的項目。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入成員`Map`，然後檢查對應是否包含它。  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]