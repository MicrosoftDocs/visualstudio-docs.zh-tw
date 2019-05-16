---
title: 查詢。Pdb 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691336"
---
# <a name="querying-the-pdb-file"></a>查詢 .Pdb 檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

程式資料庫檔案 (副檔名為.pdb) 是二進位檔案，其中包含型別和編譯及連結專案的期間所收集的符號偵錯資訊。 PDB 檔案建立時編譯 C /C++使用程式設計 **/ZI**或是 **/Zi**或[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]， [!INCLUDE[csprcs](../../includes/csprcs-md.md)]，或[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]以程式 **/偵錯**選項。 物件檔案包含到偵錯資訊的.pdb 檔案的參考。 如需有關 pdb 檔案的詳細資訊，請參閱[PDB 檔案](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f)。 DIA 應用程式可以使用下列一般步驟，以取得各種不同的符號、 物件和資料元素，在可執行檔映像中的相關詳細資料。  
  
### <a name="to-query-the-pdb-file"></a>查詢.pdb 檔案  
  
1. 藉由建立取得資料來源[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)介面。  
  
    ```cpp#  
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
  
2. 呼叫[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)或是[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)載入偵錯資訊。  
  
    ```cpp#  
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
  
3. 呼叫[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)來開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md)來存取偵錯資訊。  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. 使用中的方法`IDiaSession`來查詢資料來源中的符號。  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. 使用`IDiaEnum*`介面列舉，並掃描符號或其他項目中的偵錯資訊。  
  
    ```cpp#  
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
