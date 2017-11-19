---
title: "IDiaTable |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be24edc89328f08199316df8bdedf2ab6391907b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiatable"></a>IDiaTable
列舉 DIA 資料來源資料表。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaTable`。  
  
|方法|說明|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|擷取[IEnumVARIANT 介面](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e)這個列舉值的版本。|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|擷取資料表的名稱。|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|擷取資料表中的項目數目。|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|擷取特定的項目索引的參考。|  
  
## <a name="remarks"></a>備註  
 這個介面會實作`IEnumUnknown`Microsoft.VisualStudio.OLE.Interop 命名空間中的列舉方法。 `IEnumUnknown`列舉介面會更有效率，用於逐一查看資料表內容，比[idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)和[idiatable:: Item](../../debugger/debug-interface-access/idiatable-item.md)方法。  
  
 解譯`IUnknown`介面傳回從其中`IDiaTable::Item`方法或`Next`方法 （在 Microsoft.VisualStudio.OLE.Interop 命名空間中） 會相依於資料表的類型。 例如，如果`IDiaTable`介面代表來源的清單插入，`IUnknown`介面應該查詢的[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得此介面，藉由呼叫[idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)或[idiaenumtables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md)方法。  
  
 會實作下列介面`IDiaTable`介面 (也就是您可以查詢`IDiaTable`介面為下列介面的其中一個):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>範例  
 第一個函式， `ShowTableNames`，工作階段中會顯示所有資料表的名稱。 第二個函式， `GetTable`，搜尋所有資料表，用於實作指定的介面的資料表。 第三個函式， `UseTable`，示範如何使用`GetTable`函式。  
  
> [!NOTE]
>  `CDiaBSTR`是一個類別，包裝`BSTR`並自動處理當具現化超出範圍時釋出的字串。  
  
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
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)