---
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba4cdb5f74cedf13cfb74b5aff6d43d24534eab9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466480"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
可讓您讀取 DIA 屬性集的持續性屬性。

## <a name="syntax"></a>語法

```
IDiaPropertyStorage : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaPropertyStorage` 。

|方法|描述|
|------------|-----------------|
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|取得此集合中屬性的列舉值指標。|
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|讀取 `BOOL` 屬性集中的值。|
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|讀取 `BSTR` 屬性集中的值。|
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|讀取 `DWORD` 屬性集中的值。|
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|讀取 `LONG` 屬性集中的值。|
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|讀取屬性集內的屬性值。|
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|取得給定屬性識別碼的對應字串名稱。|
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|讀取 `ULONGLONG` 屬性集中的值。|

## <a name="remarks"></a>備註
屬性集內的每個屬性都是由屬性識別碼（ID）所識別，這是 `ULONG` 該集合唯一的四位元組值。 透過介面公開的屬性會 `IDiaPropertyStorage` 對應至父介面中可用的屬性。 例如， [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面的屬性可以透過介面以名稱來存取 `IDiaPropertyStorage` （請注意，雖然屬性可能可供存取，但它並不表示屬性對特定物件是有效的 `IDiaSymbol` ）。

## <a name="notes-for-callers"></a>呼叫者的注意事項
藉由 `QueryInterface` 在另一個介面上呼叫方法來取得此介面。 下列介面可以針對 `IDiaPropertyStorage` 介面查詢：

- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

## <a name="example"></a>範例
這個範例會顯示一個函式，該函式會顯示物件所公開的所有屬性 `IDiaPropertyStorage` 。 如需[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)如何 `IDiaPropertyStorage` 從[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)介面取得介面的範例，請參閱 IDiaEnumInjectedSources 介面。

```C++
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)
{
    IEnumSTATPROPSTG* pEnumProps;
    STATPROPSTG       prop;
    DWORD             celt = 1;

    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)
    {
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)
        {
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };
            PROPVARIANT vt = { VT_EMPTY };

            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)
            {
                switch( vt.vt ){
                    case VT_BOOL:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );
                        break;
                    case VT_I2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );
                        break;
                    case VT_UI2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );
                        break;
                    case VT_I4:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );
                        break;
                    case VT_UI4:
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );
                        break;
                    case VT_UI8:
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );
                        break;
                    case VT_BSTR:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );
                        break;
                    case VT_UNKNOWN:
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );
                        break;
                    case VT_SAFEARRAY:
                        break;
                    default:
                       break;
                }
                VariantClear((VARIANTARG*) &vt);
            }
        }
        pEnumProps->Release();
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
