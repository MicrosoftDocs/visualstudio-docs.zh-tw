---
title: 查詢。Pdb 檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a22bc8fbe65795a3c5162607a12690081e565666
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917111"
---
# <a name="querying-the-pdb-file"></a>查詢 .Pdb 檔案
程式資料庫檔案（副檔名 .pdb）是一個二進位檔案，其中包含在編譯和連結專案的過程中所收集的類型和符號的偵錯工具資訊。 當您使用C++ **/zi**或 **/zi**編譯 C/程式，或使用 **/debug**選項 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]或 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] 程式時，會建立 PDB 檔案。 物件檔案包含用於偵錯工具之 .pdb 檔案的參考。 如需 pdb 檔案的詳細資訊，請參閱[pdb](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100))檔案。 DIA 應用程式可以使用下列一般步驟來取得可執行映射內各種符號、物件和資料元素的詳細資訊。

### <a name="to-query-the-pdb-file"></a>若要查詢 .pdb 檔案

1. 藉由建立[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)介面來取得資料來源。

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. 呼叫[IDiaDataSource：： loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)或[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)以載入調試資訊。

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. 呼叫[IDiaDataSource：： openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)以開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md) ，以取得偵錯工具資訊的存取權。

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. 使用 `IDiaSession` 中的方法，查詢資料來源中的符號。

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. 使用 `IDiaEnum*` 介面來列舉和掃描所有的符號或其他的調試資訊元素。

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
