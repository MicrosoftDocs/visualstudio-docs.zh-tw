---
title: IDiaEnumLineNumbers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers interface
ms.assetid: cdf07b4f-19e4-4dcd-8af8-c2dbca586a7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d4a470a2e3037d77b07786e6f37d588162278a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856527"
---
# <a name="idiaenumlinenumbers"></a>IDiaEnumLineNumbers
列舉資料來源中包含的各種行號。

## <a name="syntax"></a>Syntax

```
IDiaEnumLineNumbers : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaEnumLineNumbers` 。

|方法|描述|
|------------|-----------------|
|[IDiaEnumLineNumbers::get__NewEnum](../../debugger/debug-interface-access/idiaenumlinenumbers-get-newenum.md)|抓取此列舉值的 [IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 版本。|
|[IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)|抓取行號的數目。|
|[IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)|以索引的方式抓取行號。|
|[IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)|捕獲列舉序列中指定的行號數目。|
|[IDiaEnumLineNumbers::Skip](../../debugger/debug-interface-access/idiaenumlinenumbers-skip.md)|略過列舉序列中指定數目的行號。|
|[IDiaEnumLineNumbers::Reset](../../debugger/debug-interface-access/idiaenumlinenumbers-reset.md)|將列舉順序重設為開頭。|
|[IDiaEnumLineNumbers::Clone](../../debugger/debug-interface-access/idiaenumlinenumbers-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫者注意事項
藉由呼叫 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 介面中的下列其中一種方法，即可取得這個介面：

- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)

- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)

- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)

- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)

- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)

## <a name="example"></a>範例
此範例顯示如何 `IDiaEnumLineNumbers` 從會話取得介面。 在此情況下，此範例會示範如何取得函式的行號列舉 (由 `pSymbol`) 表示。 如需使用行號的更完整範例，請參閱 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 介面。

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD isect = 0;
    DWORD offset = 0;
    pSymbol->get_addressSection( &isect );
    pSymbol->get_addressOffset( &offset );
    pSymbol->get_length( &length );
    if ( isect != 0 && length > 0 )
    {
        CComPtr< IDiaEnumLineNumbers > pLines;
        if ( SUCCEEDED( pSession->findLinesByAddr(
                                      isect,
                                      offset,
                                      static_cast<DWORD>( length ),
                                      &pLines )
                      )
           )
        {
            // Do something with the enumeration
        }
    }
}
```

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
