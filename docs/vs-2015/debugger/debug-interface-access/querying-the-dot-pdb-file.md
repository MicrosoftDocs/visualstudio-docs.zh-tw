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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691336"
---
# <a name="querying-the-pdb-file"></a>查詢 .Pdb 檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

程式資料庫檔案 (副檔名) 是一個二進位檔案，其中包含編譯和連結專案時所收集的型別和符號偵錯工具資訊。 當您使用 **/zi** 或 **/zi** 編譯 C/c + + 程式 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ，或 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] 使用 **/debug** 選項來編譯、或程式時，就會建立 PDB 檔案。 物件檔包含用於偵錯工具的 .pdb 檔參考。 如需 pdb 檔案的詳細資訊，請參閱 [pdb](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f)檔案。 DIA 應用程式可以使用下列一般步驟，取得可執行映射內各種符號、物件和資料元素的詳細資料。  
  
### <a name="to-query-the-pdb-file"></a>查詢 .pdb 檔案  
  
1. 藉由建立 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) 介面來取得資料來源。  
  
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
  
2. 呼叫 [IDiaDataSource：： loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 或 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 以載入調試資訊。  
  
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
  
3. 呼叫 [IDiaDataSource：： openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 來開啟 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) ，以存取偵錯工具資訊。  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. 使用中的方法 `IDiaSession` 來查詢資料來源中的符號。  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. 您 `IDiaEnum*` 可以使用介面，透過符號或其他偵錯工具的元素來列舉和掃描。  
  
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
