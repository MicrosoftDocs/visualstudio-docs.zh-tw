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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f909067c704686be4608546cc891df7f131107e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819546"
---
# <a name="querying-the-pdb-file"></a>查詢 .Pdb 檔案
程式資料庫檔案 (副檔名為.pdb) 是二進位檔案，其中包含型別和編譯及連結專案的期間所收集的符號偵錯資訊。 當您編譯的 C/c + + 程式時建立 PDB 檔案 **/ZI**或 **/Zi**或[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，或[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]程式設計 **/偵錯**選項。 物件檔案包含到偵錯資訊的.pdb 檔案的參考。 如需有關 pdb 檔案的詳細資訊，請參閱[PDB 檔案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100))。 DIA 應用程式可以使用下列一般步驟，以取得各種不同的符號、 物件和資料元素，在可執行檔映像中的相關詳細資料。  
  
### <a name="to-query-the-pdb-file"></a>查詢.pdb 檔案  
  
1.  藉由建立取得資料來源[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)介面。  
  
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
  
2.  呼叫[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)或是[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)載入偵錯資訊。  
  
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
  
3.  呼叫[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)來開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md)來存取偵錯資訊。  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  使用中的方法`IDiaSession`來查詢資料來源中的符號。  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  使用`IDiaEnum*`介面列舉，並掃描符號或其他項目中的偵錯資訊。  
  
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
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)