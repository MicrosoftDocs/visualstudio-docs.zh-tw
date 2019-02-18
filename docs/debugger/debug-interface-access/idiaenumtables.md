---
title: IDiaEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a74d0c11f6d3f7265455bd8df1d481408d8e7b
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155821"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
列舉各種資料來源中包含的資料表。

## <a name="syntax"></a>語法

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDiaEnumTables`。

|方法|描述|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|擷取[IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)這個列舉值的版本。|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|擷取資料表的數目。|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|擷取透過索引或名稱的資料表。|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|擷取指定的數目的列舉型別序列中的資料表。|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|略過指定的數目的列舉型別序列中的資料表。|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|將列舉型別序列重設到開頭。|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫端資訊
取得這個介面，藉由呼叫[idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md)方法。

## <a name="example"></a>範例
此範例示範如何取得`IDiaEnumTables`從工作階段的介面。 使用資料表的更完整範例，請參閱 < [IDiaTable](../../debugger/debug-interface-access/idiatable.md)介面。

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    // Do something with table
}
```

## <a name="requirements"></a>需求
標頭： Dia2.h

程式庫： diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>請參閱
[介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
