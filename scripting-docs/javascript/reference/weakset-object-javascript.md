---
title: WeakSet 物件 (JavaScript) |Microsoft 文件
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641598"
---
# <a name="weakset-object-javascript"></a>WeakSet 物件 (JavaScript)
可屬於任何類型的唯一物件集合。  
  
## <a name="syntax"></a>語法  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>備註  
 如果您嘗試將非唯一的物件加入 `WeakSet`，新物件不會加入集合 (Collection)。  
  
 不同於 `Set`，只有物件可以加入集合 (Collection)。 無法將任意值加入集合 (Collection)。  
  
 在`WeakSet`物件以保存 '弱' 集合中物件的參考。 這表示 `WeakSet` 不會防止物件發生記憶體回收。 當沒有物件參考時 (`WeakSet` 除外)，記憶體回收行程可能會回收物件。  
  
 `WeakSet` (或 `WeakMap`) 在需要快取物件或物件中繼資料的一些情節下可能會很有用。 例如，非可延伸物件的中繼資料可能儲存在 `WeakSet` 中，或者您可能使用 `WeakSet` 建立使用者影像的快取。  
  
## <a name="properties"></a>屬性  
 下表列出 `WeakSet` 物件的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|建構函式|指定用來建立集合的函式。|  
|原型|傳回集合的原型參考。|  
  
## <a name="methods"></a>方法  
 下表列出 `WeakSet` 物件的方法。  
  
|方法|描述|  
|------------|-----------------|  
|加入|將項目加入集合。|  
|刪除|將指定的項目從集合中移除。|  
|has|如果集合包含指定的項目，則傳回 `true`。|  
  
## <a name="example"></a>範例  
 下列範例示範如何將成員加入集合，然後檢查是否已加入這些成員。  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]