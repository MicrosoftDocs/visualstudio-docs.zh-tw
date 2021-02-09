---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe7d30fdf5c669f572c66a975494490ed7c4e954
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855260"
---
# <a name="idiasegment"></a>IDiaSegment
將區段編號的資料對應至位址空間的區段。

## <a name="syntax"></a>Syntax

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaSegment` 。

|方法|描述|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|捕獲區段編號。|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|抓取區段開始之區段中的位移。|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|捕獲區段中的位元組數目。|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|抓取指出區段是否可讀取的旗標。|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|抓取旗標，這個旗標會指出區段是否可以修改。|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|抓取指出區段是否為可執行檔的旗標。|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|抓取對應至此區段的區段編號。|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|捕獲區段開頭 (RVA) 的相對虛擬位址。|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|抓取區段開頭 (VA) 的虛擬位址。|

## <a name="remarks"></a>備註
因為 DIA SDK 已經從相對虛擬位址的區段位移執行翻譯，大部分的應用程式都不會利用區段對應中的資訊。

## <a name="notes-for-callers"></a>呼叫者注意事項
藉由呼叫 [IDiaEnumSegments：： Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) 或 [IDiaEnumSegments：： Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) 方法來取得這個介面。 如需詳細資訊，請參閱範例。

## <a name="example"></a>範例
此函式會顯示資料表中所有區段的位址，以及最接近的符號。

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

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
