---
title: 查詢。Pdb 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 3b552300926ae0448aacd084b54934f03527f81e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="querying-the-pdb-file"></a>查詢 .Pdb 檔案
程式資料庫檔案 (副檔名.pdb) 是包含類型和符號進行編譯和連結專案期間所收集的偵錯資訊的二進位檔案。 當您編譯 C/c + + 程式以建立 PDB 檔案 **/ZI**或 **/Zi**或[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，或[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]程式與**偵錯**選項。 物件的檔案包含偵錯資訊的.pdb 檔案的參考。 如需有關 pdb 檔的詳細資訊，請參閱[PDB 檔案](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f)。 DIA 應用程式可以使用下列一般步驟，以取得詳細各種符號、 物件和可執行映像中的資料元素。  
  
### <a name="to-query-the-pdb-file"></a>查詢.pdb 檔案  
  
1.  取得資料來源，藉由建立[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)介面。  
  
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
  
2.  呼叫[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)或[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)載入偵錯資訊。  
  
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
  
3.  呼叫[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md)來存取偵錯資訊。  
  
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
  
5.  使用`IDiaEnum*`介面，即可列舉和掃描整個符號或其他元素的偵錯資訊。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)