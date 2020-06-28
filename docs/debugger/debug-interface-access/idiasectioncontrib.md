---
title: IDiaSectionContrib | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82d1a52616273a1cfe1d54580c91ec4ba6e1c09e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466067"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
抓取描述區段貢獻的資料，也就是由編譯模組貢獻給影像的連續記憶體區塊。

## <a name="syntax"></a>語法

```
IDiaSectionContrib : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaSectionContrib` 。

|方法|描述|
|------------|-----------------|
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|抓取提供此區段之編譯模組符號的參考。|
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|抓取投稿位址的區段部分。|
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|抓取投稿位址的時差部分。|
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|抓取貢獻的影像相對虛擬位址（RVA）。|
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|抓取貢獻的虛擬位址（VA）。|
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|抓取區段中的位元組數目。|
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|抓取表示區段是否無法分頁到記憶體的旗標。|
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|抓取表示區段是否不應填補至下一個記憶體界限的旗標。|
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|抓取表示區段是否包含可執行程式碼的旗標。|
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|抓取表示區段是否包含16位程式碼的旗標。|
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|抓取表示區段是否包含已初始化資料的旗標。|
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|抓取表示區段是否包含未初始化資料的旗標。|
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|抓取表示區段是否包含批註或類似資訊的旗標。|
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|抓取旗標，指出是否要先移除該區段，再將它設為記憶體中影像的一部分。|
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|抓取表示區段是否為 COMDAT 記錄的旗標。|
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|抓取表示區段是否可以捨棄的旗標。|
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|抓取指出是否無法快取區段的旗標。|
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|抓取表示區段是否可以在記憶體中共用的旗標。|
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|抓取表示區段是否為程式碼之可執行檔的旗標。|
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|抓取指出是否可以讀取區段的旗標。|
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|抓取指出是否可以寫入區段的旗標。|
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|抓取區段中資料的迴圈冗余檢查（CRC）。|
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|抓取區段的重新配置資訊的 CRC。|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|抓取區段的編譯模組識別碼。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫者的注意事項
這個介面是藉由呼叫[IDiaEnumSectionContribs：： Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)和[IDiaEnumSectionContribs：： Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)方法來取得。 如需取得介面的範例，請參閱[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)介面 `IDiaSectionContrib` 。

## <a name="example"></a>範例
此函式會顯示每個區段的位址以及任何相關聯的符號。 請參閱[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)介面，以瞭解如何 `IDiaSectionContrib` 取得介面。

```C++
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)
{
    if (pSecContrib != NULL && pSession != NULL)
    {
        DWORD rva;
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )
        {
            printf( "\taddr: 0x%.8X", rva );
            pSecContrib = NULL;
            CComPtr<IDiaSymbol> pSym;
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
            {
                CDiaBSTR name;
                DWORD    tag;
                pSym->get_symTag( &tag );
                pSym->get_name( &name );
                printf( "     symbol: %ws (%ws)\n",
                        name != NULL ? name : L"",
                        szTags[ tag ] );
            }
            else
            {
                printf( "<no symbol found?>\n" );
            }
        }
        else
        {
            DWORD isect;
            DWORD offset;
            pSecContrib->get_addressSection( &isect );
            pSecContrib->get_addressOffset( &offset );
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );
            pSecContrib = NULL;
            CComPtr<IDiaSymbol> pSym;
            if ( SUCCEEDED( psession->findSymbolByAddr(
                                              isect,
                                              offset,
                                              SymTagNull,
                                              &pSym )
                          )
               )
            {
                CDiaBSTR name;
                DWORD    tag;
                pSym->get_symTag( &tag );
                pSym->get_name( &name );
                printf( "     symbol: %ws (%ws)\n",
                    name != NULL ? name : L"",
                    szTags[ tag ] );
            }
            else
            {
                printf( "<no symbol found?>\n" );
            }
        }
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)
- [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
