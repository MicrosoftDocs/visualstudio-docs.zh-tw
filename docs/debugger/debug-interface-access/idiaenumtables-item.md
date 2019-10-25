---
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743758"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
藉由索引或名稱來抓取資料表。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>參數
 `index`

在要抓取之[IDiaTable](../../debugger/debug-interface-access/idiatable.md)的索引或名稱。 如果使用整數變體，它必須在0到 `count`-1 的範圍內，其中 `count` 是[IDiaEnumTables：： get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)方法所傳回的。

 `table`

脫銷傳回[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件，代表所需的資料表。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果指定了字串 variant，則字串會命名特定的資料表。 名稱應該是常數中所定義的其中一個資料表名稱[（Debug Interface ACCESS SDK）](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)。

## <a name="example"></a>範例

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)