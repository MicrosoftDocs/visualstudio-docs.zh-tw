---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dfb0330f08dab158c298bbc944d8dc6410f719f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839429"
---
# <a name="idiasegment"></a>IDiaSegment
對應至區段的位址空間資料區段數目。

## <a name="syntax"></a>語法

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法`IDiaSegment`。

|方法|描述|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|擷取的區段數目。|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|擷取一節的開始處的區段中的位移。|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|擷取區段中的位元組的數目。|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|擷取旗標，指出是否可以讀取區段。|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|擷取旗標，指出是否可以修改的區段。|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|擷取指出區段是否可執行檔的旗標。|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|擷取對應至這個區段的區段數目。|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|擷取區段開頭的相對虛擬位址 (RVA)。|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|擷取區段開頭的虛擬位址 (VA)。|

## <a name="remarks"></a>備註
DIA SDK 已經從區段位移，翻譯執行相對虛擬位址，因為大部分的應用程式不會使用區段對應中的資訊。

## <a name="notes-for-callers"></a>呼叫端資訊
取得這個介面，藉由呼叫[idiaenumsegments:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)或是[idiaenumsegments:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)方法。 請參閱詳細資料的範例。

## <a name="example"></a>範例
此函式會顯示所有區段的位址中的資料表和最接近的符號。

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSegments ),
                               (void**)&pSegments )
                  )
       )
    {
        CComPtr<IDiaSegment> pSegment;
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&
                celt == 1 )
        {
            DWORD rva;
            DWORD seg;

            pSegment->get_addressSection( &seg );
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )
            {
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );
                pSegment = NULL;

                CComPtr<IDiaSymbol> pSym;
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
                {
                    CDiaBSTR name;
                    DWORD    tag;

                    pSym->get_symTag( &tag );
                    pSym->get_name( &name );
                    printf( "\tClosest symbol: %ws (%ws)\n",
                            name != NULL ? name : L"",
                            szTags[ tag ] );
                }
            }
        }
    }
}
```

## <a name="requirements"></a>需求
標頭：dia2.h

程式庫： diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
