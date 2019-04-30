---
title: IDiaTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6109e2eeb94481a2bff4a6467c490ec656d4c2f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442006"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

列舉 DIA 資料來源資料表。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaTable`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|擷取[IEnumVARIANT 介面](http://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e)這個列舉值的版本。|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|擷取資料表的名稱。|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|擷取資料表中的項目數。|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|擷取特定項目索引的參考。|  
  
## <a name="remarks"></a>備註  
 這個介面會實作`IEnumUnknown`Microsoft.VisualStudio.OLE.Interop 命名空間中的列舉方法。 `IEnumUnknown`列舉型別介面會逐一查看資料表內容比更有效率[idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)並[idiatable:: Item](../../debugger/debug-interface-access/idiatable-item.md)方法。  
  
 解譯`IUnknown`介面傳回從其中`IDiaTable::Item`方法或`Next`方法 （在 Microsoft.VisualStudio.OLE.Interop 命名空間中） 會相依於資料表的類型。 例如，如果`IDiaTable`介面代表插入的來源清單`IUnknown`介面應該查詢[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫[idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)或是[idiaenumtables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md)方法。  
  
 以實作下列介面`IDiaTable`介面 (也就是您可以查詢`IDiaTable`其中一個下列介面的介面):  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>範例  
 第一個函式， `ShowTableNames`，工作階段中會顯示所有資料表的名稱。 第二個函式， `GetTable`，搜尋所有實作指定的介面的資料表中的資料表。 第三個函式中， `UseTable`，示範如何使用`GetTable`函式。  
  
> [!NOTE]
> `CDiaBSTR` 是一個類別，包裝`BSTR`並可自動處理具現化超出範圍時釋出的字串。  
  
```cpp#  
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
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
