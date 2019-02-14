---
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7257301616c40735f31df3cd777e16e8cf0bd71c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026355"
---
# <a name="idiasession"></a>IDiaSession
提供偵錯符號的查詢內容。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDiaSession`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|擷取對應至這個符號存放區中的符號的可執行檔載入位址。 這是相同的值傳遞給`put_loadAddress`方法。|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|符號設定對應的可執行檔載入位址，此符號存放區中。 **注意：** 請務必呼叫這個方法，當您取得`IDiaSession`物件，並開始使用物件之前。|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|擷取至全域範圍的參考。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|擷取包含在符號存放區中的所有資料表的列舉值。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|擷取靜態位置的所有具名符號的列舉值。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|擷取指定的父識別碼的所有相符的名稱和符號類型的子系。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|擷取指定的符號類型包含此項目，或最接近，指定的位址。|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|擷取包含此項目，或指定相對虛擬位址 (RVA) 到最接近指定的符號類型。|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|擷取包含此項目，或指定的虛擬位址 (VA) 到最接近指定的符號類型。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|擷取包含指定之中繼資料語彙基元的符號。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|檢查兩個符號是否相等。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|擷取符號依其唯一識別碼。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|擷取包含此項目，或指定的相對虛擬位址和位移至最接近指定的符號類型。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|擷取包含此項目，或指定的虛擬位址和位移至最接近指定的符號類型。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|擷取原始程式檔編譯模組和名稱。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|依來源檔案識別碼擷取原始程式檔。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|擷取指定的編譯模組和來源檔案識別碼內的行號。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|擷取指定的編譯模組中的行，其中包含指定的位址。|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|擷取指定的編譯模組中的行，其中包含指定的相對虛擬位址。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|尋找包含在指定的位址範圍中的行的行號資訊。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|擷取在指定的編譯模組的原始程式檔和行號的行。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|擷取已放入符號存放區的屬性提供者或編譯處理程序的其他元件的來源。|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|擷取偵錯資料流的列舉的順序。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|擷取列舉型別，可讓用戶端來逐一查看所有指定的位址上的內嵌框架。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|擷取列舉型別，可讓用戶端來逐一查看所有內嵌上的框架指定相對虛擬位址 (RVA)。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|擷取列舉型別，可讓用戶端來逐一查看所有指定的虛擬位址 (VA) 上的內嵌框架。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|擷取列舉型別，可讓用戶端來逐一查看所有函式是內嵌的直接或間接由指定之父代符號的行號資訊。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|擷取可讓用戶端來逐一查看所有函式是內嵌的直接或間接由指定之父代符號的行號資訊，而且包含在指定的位址範圍的列舉。|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|擷取列舉型別，可讓用戶端來逐一查看所有函式是內嵌的直接或間接由指定之父代符號的行號資訊，而且包含在指定相對的虛擬位址 (RVA)。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|擷取列舉型別，可讓用戶端來逐一查看所有函式是內嵌的直接或間接由指定之父代符號的行號資訊，而且包含在指定的虛擬位址 (VA)。|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|擷取列舉型別，可讓用戶端來逐一查看所有函式是內嵌，直接或間接地在 指定的來源檔案和行號的行號資訊。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|擷取列舉型別，可讓用戶端來逐一查看所有符合指定之名稱的內嵌函式行號資訊。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|父項加速器虛設常式的函式中傳回指定的標記值會對應到變數的符號的列舉。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|指定對應的標記值，這個方法會傳回包含符號的列舉型別函式中指定的父加速器虛設常式在指定的相對虛擬位址。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|傳回對應到指定的內嵌函式名稱的內嵌框架的符號的列舉。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|傳回對應的內嵌框架的符號的列舉型別到指定的來源位置。|  
  
## <a name="remarks"></a>備註  
 請務必呼叫[idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法之後建立`IDiaSession`物件，和傳遞給的值`put_loadAddress`方法必須為非零 — 為符號的任何虛擬位址 (VA) 屬性可存取。 載入位址來自於載入的任何程式正在偵錯的可執行檔。 例如，您可以呼叫 Win32 函式`GetModuleInformation`擷取的載入位址的可執行檔，指定可執行檔的控制代碼。  
  
## <a name="example"></a>範例  
 此範例示範如何取得`IDiaSession`DIA SDK 一般初始化介面。  
  
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
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)