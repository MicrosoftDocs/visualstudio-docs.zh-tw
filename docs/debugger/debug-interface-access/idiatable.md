---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 984b9d5d9bfd5c3800ec816e1f57489e0348f53c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461284"
---
# <a name="idiatable"></a>IDiaTable
列舉 DIA 的資料來源資料表。

## <a name="syntax"></a>語法

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaTable` 。

|方法|描述|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|抓取此列舉值的[IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)版本。|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|抓取資料表的名稱。|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|抓取資料表中的專案數。|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|抓取特定專案索引的參考。|

## <a name="remarks"></a>備註
這個介面會 `IEnumUnknown` 在 VisualStudio 命名空間中執行列舉方法。 `IEnumUnknown`列舉介面比[IDiaTable：： Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)和[IDiaTable：： Item](../../debugger/debug-interface-access/idiatable-item.md)方法反覆運算資料表內容更有效率。

`IUnknown`從 `IDiaTable::Item` 方法或 `Next` 方法（在 VisualStudio 命名空間中）傳回之介面的轉譯取決於資料表的類型。 例如，如果 `IDiaTable` 介面代表插入的來源清單，則 `IUnknown` 應該針對[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)介面查詢介面。

## <a name="notes-for-callers"></a>呼叫者的注意事項
藉由呼叫[IDiaEnumTables：： Item](../../debugger/debug-interface-access/idiaenumtables-item.md)或[IDiaEnumTables：： Next](../../debugger/debug-interface-access/idiaenumtables-next.md)方法來取得此介面。

下列介面會使用介面來執行 `IDiaTable` （也就是，您可以查詢 `IDiaTable` 介面以取得下列其中一個介面）：

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>範例
第一個函式會 `ShowTableNames` 顯示會話中所有資料表的名稱。 第二個函式會 `GetTable` 搜尋所有資料表，尋找可執行指定介面的資料表。 第三個函式會 `UseTable` 顯示如何使用 `GetTable` 函數。

> [!NOTE]
> `CDiaBSTR`是包裝的類別，當具現 `BSTR` 化超出範圍時，會自動處理釋放字串。

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

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
