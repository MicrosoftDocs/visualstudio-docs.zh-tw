---
title: add 方法 (Set) (JavaScript) |Microsoft 文件
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633168"
---
# <a name="add-method-set-javascript"></a>add 方法 (Set) (JavaScript)
將新項目加入至集合 (Set)。  
  
## <a name="syntax"></a>語法  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>參數  
 `setObj`  
 必要項。 `Set` 物件。  
  
 `value`  
 必要項。 `Set` 的新項目。  
  
## <a name="remarks"></a>備註  
 新項目可以是任何類型，而且必須是唯一的。 如果您將非唯一的項目加入至 `Set`，新項目不會加入至集合 (Collection)。  
  
## <a name="example"></a>範例  
 下面範例會示範如何將成員加入至集合 (Set)，然後擷取這些成員。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]