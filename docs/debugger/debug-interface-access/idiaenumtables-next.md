---
description: 捕獲列舉序列中指定的資料表數目。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdc207633a083e841221e3c6ca527c7ffb3dbcf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157879"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
捕獲列舉序列中指定的資料表數目。

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

在要抓取的列舉值中的資料表數目。

 `rgelt`

擴展要填入 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 物件的陣列，這些物件代表所需的資料表。

 `pceltFetched`

擴展傳回已提取列舉值中的資料表數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他資料表，則會傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
