---
title: "IDiaDataSource |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51a277d9ff1bf190aa87d7c4e9d8d852f8c38323
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasource"></a>IDiaDataSource
啟始的存取權的偵錯符號的來源。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaDataSource`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|擷取最後一個載入錯誤的檔案名稱。|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|隨即開啟，並準備做為偵錯資料來源的程式資料庫 (.pdb) 檔案。|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|會開啟，並驗證的程式資料庫 (.pdb) 檔案符合提供; 的簽章資訊準備的.pdb 檔做為偵錯資料來源。|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|隨即開啟，並準備.exe/.dll 檔案相關聯的偵錯資料。|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|準備儲存在記憶體中的資料流透過存取程式資料庫 (.pdb) 檔案的偵錯資料。|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|開啟查詢符號的工作階段。|  
  
## <a name="remarks"></a>備註  
 呼叫其中一個 load 方法`IDiaDataSource`介面便會開啟符號來源。 在成功呼叫[idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)方法會傳回[IDiaSession](../../debugger/debug-interface-access/idiasession.md)支援查詢資料來源的介面。 如果負載方法會傳回與檔案相關的錯誤則[idiadatasource:: Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)方法傳回值包含與錯誤相關聯的檔案名稱。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面透過呼叫`CoCreateInstance`函式的類別識別項與`CLSID_DiaSource`而介面 ID 的`IID_IDiaDataSource`。 此範例示範如何取得此介面。  
  
## <a name="example"></a>範例  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)