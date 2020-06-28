---
title: IDiaEnumTables::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d425e16e18338c0269ccbf88030a47c7b184507
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467523"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
抓取列舉序列中指定數目的資料表。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>參數
 `celt`

在列舉值中要抓取的資料表數目。

 `rgelt`

脫銷要填入的陣列，其中包含代表所需資料表的[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件。

 `pceltFetched`

脫銷傳回已提取枚舉器中的資料表數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他資料表，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)