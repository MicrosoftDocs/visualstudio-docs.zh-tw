---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7fb8c5336a14180b3742fa02a91e6532b6e5831
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465346"
---
# <a name="idiasession"></a>IDiaSession
提供 debug 符號的查詢內容。

## <a name="syntax"></a>語法

```
IDiaSession : IUnknown
```

## <a name="methods"></a>方法
下表顯示的方法 `IDiaSession` 。

|方法|描述|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|抓取可執行檔的載入位址，此檔案會對應至這個符號存放區中的符號。 這是傳遞給方法的相同值 `put_loadAddress` 。|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|設定可執行檔的載入位址，該檔案會對應到此符號存放區中的符號。 **注意：** 當您取得 `IDiaSession` 物件，以及開始使用物件之前，請務必呼叫這個方法。|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|抓取全域範圍的參考。|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|抓取符號存放區中包含的所有資料表的列舉值。|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|抓取靜態位置中所有命名符號的列舉值。|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|抓取符合名稱和符號類型之指定父系識別碼的所有子系。|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|抓取指定的符號類型，其中包含或最接近指定的位址。|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|抓取指定的符號類型，其中包含或最接近指定的相對虛擬位址（RVA）。|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|抓取指定的符號類型，其中包含或最接近指定的虛擬位址（VA）。|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|抓取包含指定之元資料標記的符號。|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|檢查兩個符號是否相等。|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|依其唯一識別碼抓取符號。|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|抓取指定的符號類型，其中包含或最接近指定的相對虛擬位址和位移。|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|抓取指定的符號類型，其中包含或最接近指定的虛擬位址和位移。|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|依編譯模組和名稱來抓取原始程式檔。|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|依來源檔案識別碼抓取原始程式檔。|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|抓取指定編譯模組和原始程式檔識別碼內的行號。|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|抓取指定編譯模組中包含指定位址的行。|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|抓取指定編譯模組中，包含指定之相對虛擬位址的行。|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|尋找指定的位址範圍所包含之行的行號資訊。|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|依原始程式檔和行號，抓取指定編譯模組中的行。|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|抓取屬性提供者或編譯進程的其他元件已放入符號存放區中的來源。|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|抓取 debug 資料流程的列舉序列。|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|抓取列舉型別，可讓用戶端逐一查看指定位址上的所有內嵌框架。|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|抓取列舉型別，可讓用戶端逐一查看指定的相對虛擬位址（RVA）上的所有內嵌框架。|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|抓取列舉型別，可讓用戶端逐一查看指定虛擬位址（VA）上的所有內嵌框架。|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|抓取列舉型別，可讓用戶端逐一查看由指定的父符號直接或間接內嵌之所有函式的行號資訊。|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|抓取列舉型別，可讓用戶端逐一查看由指定的父符號內嵌、直接或間接內嵌之所有函式的行號資訊，並包含在指定的位址範圍內。|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|抓取列舉型別，可讓用戶端逐一查看由指定的父符號內嵌、直接或間接內嵌之所有函式的行號資訊，並包含在指定的相對虛擬位址（RVA）內。|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|抓取列舉型別，可讓用戶端逐一查看由指定的父符號內嵌、直接或間接內嵌之所有函式的行號資訊，並包含在指定的虛擬位址（VA）中。|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|抓取列舉型別，可讓用戶端逐一查看指定的原始程式檔和行號中，直接或間接內嵌之所有函式的行號資訊。|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|抓取列舉型別，可讓用戶端逐一查看所有符合指定名稱之內嵌函式的行號資訊。|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|針對指定的標記值在父快速鍵 stub 函數中對應的變數，傳回符號的列舉。|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|假設有對應的標記值，這個方法會傳回指定的相對虛擬位址上，包含在指定之父加速器 stub 函數中的符號列舉。|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|針對對應至指定之內嵌函數名稱的內嵌框架，傳回符號的列舉。|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|針對對應至指定來源位置的內嵌框架，傳回符號的列舉。|

## <a name="remarks"></a>備註
在建立物件之後，請務必呼叫[IDiaSession：:p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法， `IDiaSession` 而傳遞給方法的值必須為 `put_loadAddress` 非零，才能存取符號的任何虛擬位址（VA）屬性。 載入位址來自于載入所要調試之可執行檔的任何程式。 例如，您可以呼叫 Win32 函數，以取得可執行檔的 `GetModuleInformation` 控制碼，以抓取可執行檔的載入位址。

## <a name="example"></a>範例
這個範例示範如何在 DIA SDK 的 `IDiaSession` 一般初始化中取得介面。

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
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Convert.exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
