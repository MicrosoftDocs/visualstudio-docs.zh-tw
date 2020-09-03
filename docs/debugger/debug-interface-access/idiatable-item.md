---
title: IDiaTable：： Item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 18efd1113d66d36b99dd33eb3e79cb0cc7e8bb05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461298"
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

在 `count` `count` [IDiaTable：： get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)方法所傳回之範圍0到-1 之資料表專案的索引。

 `element`

擴展傳回 `IUnknown` 物件，該物件表示指定的資料表專案。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 資料表代表物件的集合。 根據這些物件，element 參數可以轉換為適當的介面。 例如，如果資料表包含 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 物件，則 element 參數可以轉換為 `IDiaSegment` 介面。

 這是 `QueryInterface` 在 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 介面中針對適當的列舉值介面呼叫方法較常見的方法，並使用列舉值的特定方法來存取資料表內容。 如需範例，請參閱 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 介面。

## <a name="see-also"></a>另請參閱
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)