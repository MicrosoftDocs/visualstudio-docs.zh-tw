---
title: IDiaEnumSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6710ebfec5f0c76bee217f9f75fb24c7efabd18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856100"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
列舉資料來源中包含的各種符號。

## <a name="syntax"></a>Syntax

```
IDiaEnumSymbols : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaEnumSymbols` 。

|方法|描述|
|------------|-----------------|
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|抓取 `IEnumVARIANT Interface` 此列舉值的版本。|
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|抓取符號的數目。|
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|藉由索引來抓取符號。|
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|抓取列舉序列中指定的符號數目。|
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|略過列舉序列中指定數目的符號。|
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|將列舉順序重設為開頭。|
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|

## <a name="remarks"></a>備註
此介面提供依特定符號類型分組的符號，例如 `SymTagUDT` (使用者定義類型) 或 `SymTagBaseClass` 。 若要使用依位址分組的符號，請使用 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
藉由呼叫下列方法來取得此介面：

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)

## <a name="example"></a>範例
這個範例會示範如何取得 `IDiaEnumSymbols` 介面，然後使用該列舉來列出使用者定義型別 (udt) 。

> [!NOTE]
> `CDiaBSTR` 是一個類別，會在具現 `BSTR` 化超出範圍時，包裝和自動處理釋出字串。

```C++
void ShowUDTs(IDiaSymbol *pGlobals)
{
    CComPtr<IDiaEnumSymbols> pEnum;
    CComPtr<IDiaSymbol> pSymbol;
    HRESULT hr;

    hr = pGlobals->findChildren(SymTagUDT,
                                NULL,
                                nsfCaseInsensitive | nsfUndecoratedName,
                                &pEnum);
    if (hr == S_OK)
    {
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR name;
            if ( pSymbol->get_name( &name ) != S_OK )
                Fatal( "get_name" );
            printf( "Found UDT: %ws\n", name );
            pSymbol = 0;
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
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
