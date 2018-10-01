---
title: IDiaPropertyStorage |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 009e90e5496031e4810e318e1ceecf506dd5c7c2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492237"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaPropertyStorage](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage)。  
  
可讓您讀取 DIA 屬性集的持續性的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaPropertyStorage`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|取得列舉值的指標，在這個集合中的屬性。|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|讀取`BOOL`屬性集合中的值。|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|讀取`BSTR`屬性集合中的值。|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|讀取`DWORD`屬性集合中的值。|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|讀取`LONG`屬性集合中的值。|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|讀取屬性值在屬性集。|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|取得對應的字串名稱指定屬性識別碼。|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|讀取`ULONGLONG`屬性集合中的值。|  
  
## <a name="remarks"></a>備註  
 屬性集內的每一個屬性由屬性識別碼 (ID)，四個位元組`ULONG`特有該組的值。 透過公開的屬性`IDiaPropertyStorage`介面對應至父介面中可用的屬性。 比方說的屬性[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面可以透過名稱存取`IDiaPropertyStorage`介面 (請注意，即使屬性可能是可存取，並不表示該屬性無效，特定`IDiaSymbol`物件)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫`QueryInterface`上另一個介面的方法。 可以查詢下列介面`IDiaPropertyStorage`介面：  
  
-   [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
-   [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
-   [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
-   [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
-   [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
-   [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
-   [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## <a name="example"></a>範例  
 此範例示範會顯示所公開的所有屬性的函式`IDiaPropertyStorage`物件。 請參閱[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面，如需如何的範例`IDiaPropertyStorage`介面取自[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)介面。  
  
```cpp#  
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
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



