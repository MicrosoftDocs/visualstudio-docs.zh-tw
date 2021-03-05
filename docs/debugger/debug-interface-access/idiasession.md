---
description: 提供 debug 符號的查詢內容。
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fc8e3b69321e89959ea2367488e4601269834d3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156962"
---
# <a name="idiasession"></a>IDiaSession
提供 debug 符號的查詢內容。

## <a name="syntax"></a>Syntax

```
IDiaSession : IUnknown
```

## <a name="methods"></a>方法
下表顯示的方法 `IDiaSession` 。

|方法|描述|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|抓取對應于此符號存放區中符號的可執行檔的載入位址。 這與傳遞給方法的值相同 `put_loadAddress` 。|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|設定可執行檔的載入位址，這些檔案會對應到此符號存放區中的符號。 **注意：**  當您取得 `IDiaSession` 物件，以及開始使用物件之前，請務必呼叫這個方法。|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|抓取全域範圍的參考。|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|抓取符號存放區中包含的所有資料表的列舉值。|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|在靜態位置抓取所有命名符號的列舉值。|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|抓取符合名稱和符號類型之指定父識別碼的所有子系。|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|抓取指定的符號類型，其中包含或最接近指定的位址。|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|抓取指定的符號類型，其中包含或最接近指定的相對虛擬位址 (RVA) 。|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|抓取指定的符號類型，其中包含或最接近指定的虛擬位址 (VA) 。|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|抓取包含指定之元資料標記的符號。|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|查看兩個符號是否相等。|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|依其唯一識別碼抓取符號。|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|抓取指定的符號類型，其中包含或最接近指定的相對虛擬位址和位移。|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|抓取指定的符號類型，其中包含或最接近指定的虛擬位址和位移。|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|依編譯單位和名稱抓取原始程式檔。|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|依來源檔案識別碼抓取原始程式檔。|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|抓取指定編譯單位和來源檔案識別碼內的行號。|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|抓取指定編譯單位中包含指定之位址的行。|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|抓取指定編譯單位中包含指定相對虛擬位址的行。|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|尋找指定位址範圍內所含行的行號資訊。|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|依原始程式檔和行號抓取指定編譯單位中的行。|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|抓取屬性提供者或編譯器的其他元件已放入符號存放區中的來源。|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|抓取 debug 資料流程的列舉序列。|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|抓取可讓用戶端逐一查看指定位址上所有內嵌框架的列舉。|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|抓取列舉，可讓用戶端在指定的相對虛擬位址 (RVA) 上，逐一查看所有的內嵌框架。|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|抓取列舉，可讓用戶端逐一查看指定虛擬位址的所有內嵌框架 (VA) 。|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|抓取列舉，此列舉可讓用戶端逐一查看由指定的父系符號，直接或間接內嵌的所有函式的行號資訊。|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|抓取列舉，此列舉可讓用戶端逐一查看由指定的父系符號內嵌、直接或間接內嵌之所有函式的行號資訊，並且包含在指定的位址範圍內。|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|抓取列舉，此列舉可讓用戶端逐一查看由指定的父系符號內嵌、直接或間接內嵌的所有函式的行號資訊，並且包含在指定的相對虛擬位址 (RVA) 內。|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|抓取列舉，此列舉可讓用戶端逐一查看由指定的父系符號內嵌、直接或間接內嵌的所有函式的行號資訊，並將其包含在指定的虛擬位址 (VA) 內。|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|抓取列舉，可讓用戶端逐一查看在指定的原始程式檔和行號中，直接或間接內嵌的所有函式的行號資訊。|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|抓取列舉，可讓用戶端逐一查看所有符合指定名稱的內嵌函式的行號資訊。|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|傳回指定之標記值在父快速鍵對應存根函式中對應之變數的符號列舉。|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|如果有對應的標記值，這個方法會傳回在指定的相對虛擬位址之指定的父加速器存根函式中所包含的符號列舉。|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|傳回對應至指定內嵌函式名稱之內嵌框架的符號列舉。|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|傳回對應至指定來源位置之內嵌框架的符號列舉。|

## <a name="remarks"></a>備註
在建立物件之後，請務必呼叫 [IDiaSession：:p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) 方法， `IDiaSession` 而傳遞給該方法的值 `put_loadAddress` 必須為非零—針對任何虛擬位址 (VA) 要存取的符號屬性。 載入位址來自任何程式，載入要進行調試的可執行檔。 例如，您可以呼叫 Win32 函數 `GetModuleInformation` ，以取得可執行檔的控制碼，以抓取可執行檔的載入位址。

## <a name="example"></a>範例
此範例示範如何在 `IDiaSession` DIA SDK 的一般初始化過程中取得介面。

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

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
