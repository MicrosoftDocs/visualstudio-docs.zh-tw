---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738703"
---
# <a name="idiatable"></a>IDiaTable
列舉 DIA 的資料來源資料表。

## <a name="syntax"></a>語法

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示 `IDiaTable` 的方法。

|方法|描述|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|抓取此列舉值的[IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)版本。|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|抓取資料表的名稱。|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|抓取資料表中的專案數。|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|抓取特定專案索引的參考。|

## <a name="remarks"></a>備註
這個介面會在 VisualStudio 命名空間中，實作為 `IEnumUnknown` 列舉方法。 @No__t_0 列舉介面比[IDiaTable：： get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)和[IDiaTable：： Item](../../debugger/debug-interface-access/idiatable-item.md)方法反復執行資料表內容更有效率。

從 `IDiaTable::Item` 方法或 `Next` 方法（在 VisualStudio 命名空間中）傳回之 `IUnknown` 介面的解讀取決於資料表的類型。 例如，如果 `IDiaTable` 介面代表插入的來源清單，則應該針對[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)介面查詢 `IUnknown` 介面。

## <a name="notes-for-callers"></a>呼叫者的注意事項
藉由呼叫[IDiaEnumTables：： Item](../../debugger/debug-interface-access/idiaenumtables-item.md)或[IDiaEnumTables：： Next](../../debugger/debug-interface-access/idiaenumtables-next.md)方法來取得此介面。

下列介面會使用 `IDiaTable` 介面來執行（也就是，您可以查詢下列其中一個介面的 `IDiaTable` 介面）：

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>範例
第一個函數 `ShowTableNames`，會顯示會話中所有資料表的名稱。 第二個函式 `GetTable`，會在所有資料表中搜尋可執行指定介面的資料表。 第三個函式 `UseTable`，會顯示如何使用 `GetTable` 函數。

> [!NOTE]
> `CDiaBSTR` 是包裝 `BSTR` 的類別，而且當具現化超出範圍時，會自動處理釋放字串。

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
