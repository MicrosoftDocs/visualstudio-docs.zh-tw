---
title: IDiaSession |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2791f318a921a25535d5e9a8f17e2c595f1f56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiasession"></a>IDiaSession
提供偵錯符號的查詢內容。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDiaSession`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|擷取對應至這個符號存放區中的符號的可執行檔的負載位址。 這是相同的值傳遞給`put_loadAddress`方法。|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|符號設定載入位址，對應的可執行檔，此符號存放區中。 **注意：**請務必呼叫這個方法，當您取得`IDiaSession`物件，並開始使用物件之前。|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|擷取全域範圍的參考。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|擷取包含在符號存放區中的所有資料表的列舉值。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|擷取靜態位置的所有具名符號的列舉值。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|擷取符合的名稱和符號類型指定的父系識別碼的所有子系。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|擷取指定的符號類型包含此項目，或最接近，指定的位址。|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|擷取指定的符號類型包含此項目，或最接近到指定的相對虛擬位址 (RVA)。|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|擷取包含此項目，或指定的虛擬位址 (VA) 到最接近指定的符號類型。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|擷取包含指定的中繼資料語彙基元的符號。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|檢查兩個符號是否相等。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|擷取符號依其唯一的識別項。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|擷取包含此項目，或最接近指定的相對虛擬位址和位移至指定的符號類型。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|擷取包含此項目，或最接近指定的虛擬位址和位移至指定的符號類型。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|擷取原始程式檔的編譯模組和名稱。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|擷取的原始程式檔的原始檔識別項。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|擷取指定的編譯和來源檔識別項中的行號。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|擷取含有指定的位址中指定的編譯模組的行。|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|擷取含有指定的相對虛擬位址中指定的編譯模組的行。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|尋找指定的位址範圍內的行的行號資訊。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|擷取的來源檔案和行號指定編譯模組中的程式。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|擷取已放入符號存放區屬性提供者或編譯程序的其他元件的來源。|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|擷取列舉的順序，偵錯資料流。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|擷取列舉，可讓用戶端來逐一查看所有指定的位址上的內嵌框架。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|擷取列舉，可讓用戶端來逐一查看所有指定相對虛擬位址 (RVA) 上的內嵌框架。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|擷取列舉，可讓用戶端來逐一查看所有指定的虛擬位址 (VA) 上的內嵌框架。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|擷取可讓用戶端來逐一查看的所有函式內嵌，直接或間接地以指定的父符號的行號資訊的列舉。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|擷取可讓用戶端來逐一查看的所有函式內嵌，直接或間接地以指定的父符號的行號資訊，而且包含在指定的位址範圍的列舉。|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|擷取列舉，可讓用戶端來逐一查看的所有函式內嵌，直接或間接地以指定的父符號的行號資訊，而且包含在指定相對的虛擬位址 (RVA)。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|擷取可讓用戶端來逐一查看的所有函式內嵌，直接或間接地以指定的父符號的行號資訊和指定的虛擬位址 (VA) 內所包含的列舉。|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|擷取可讓用戶端來逐一查看的所有函式是內嵌的直接或間接地中指定的來源檔案和行號的行號資訊的列舉。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|擷取可讓用戶端來逐一查看的所有符合指定的名稱的內嵌函式的行號資訊的列舉。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|父系 Accelerator 虛設常式函式中傳回符號的變數指定的標記值對應至的列舉。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|指定對應的標記值，這個方法會傳回列舉包含的符號的函式中指定的父 Accelerator 虛設常式在指定的相對虛擬位址。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|傳回對應至指定的內嵌函式名稱的內嵌框架的符號的列舉。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|傳回指定的來源位置對應的內嵌框架的符號的列舉型別。|  
  
## <a name="remarks"></a>備註  
 請務必呼叫[idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法之後建立`IDiaSession`物件 — 和值傳遞至`put_loadAddress`方法必須為非零 — 針對符號的任何虛擬位址 (VA) 屬性可存取。 載入偵錯的可執行檔的任何程式來自負載位址。 例如，您可以呼叫 Win32 函式`GetModuleInformation`擷取控制代碼提供的可執行檔的可執行檔，載入地址。  
  
## <a name="example"></a>範例  
 這個範例示範如何取得`IDiaSession`介面做為一般初始化 DIA SDK 的一部分。  
  
```C++  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)