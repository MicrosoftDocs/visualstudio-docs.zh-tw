---
title: IDiaTable：： Item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738719"
---
# <a name="idiatableitem"></a>IDiaTable::Item
抓取資料表中所指定專案的參考。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>參數
 `index`

在資料表專案的索引，範圍從0到 `count`-1，其中 `count` 是由[IDiaTable：： get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)方法所傳回。

 `element`

脫銷傳回代表指定之資料表專案的 `IUnknown` 物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 資料表代表物件的集合。 視這些物件而定，element 參數可以轉換成適當的介面。 例如，如果資料表包含[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件，則 element 參數可以轉換成 `IDiaSegment` 介面。

 在[IDiaTable](../../debugger/debug-interface-access/idiatable.md)介面中為適當的列舉值介面呼叫 `QueryInterface` 方法是較常見的方法，並使用列舉值的特定方法來存取資料表的內容。 如需範例，請參閱[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面。

## <a name="see-also"></a>請參閱
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)