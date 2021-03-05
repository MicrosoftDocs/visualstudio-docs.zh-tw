---
description: 藉由索引或名稱抓取資料表。
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc222672b0ba52f19f153a8e0c9e97137a069607
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148574"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
藉由索引或名稱抓取資料表。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>參數
 `index`

在要抓取之 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 的索引或名稱。 如果使用整數變異數，它必須在0到-1 的範圍內 `count` ，其中 `count` 是 [IDiaEnumTables：： get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) 方法所傳回的。

 `table`

擴展傳回代表所需資料表的 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 如果指定了字串變數，則字串會命名為特定的資料表。 名稱應該是常數中所定義的其中一個資料表名稱 [ (Debug Interface ACCESS SDK) ](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)。

## <a name="example"></a>範例

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
