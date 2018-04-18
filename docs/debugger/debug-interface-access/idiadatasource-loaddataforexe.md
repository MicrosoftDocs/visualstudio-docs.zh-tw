---
title: 'Idiadatasource:: Loaddataforexe |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e9e68acd3b8c87bb3fa7a609380a2afe8bb9bee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
隨即開啟，並準備.exe/.dll 檔案相關聯的偵錯資料。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>參數  
 可執行檔  
 [in].Exe 或.dll 檔案路徑。  
  
 searchPath  
 [in]要搜尋的偵錯資料的替代路徑。  
  
 pCallback  
 [in]`IUnknown`介面之物件的支援偵錯回呼介面，例如[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)， [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)、 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)，及/或[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示一些可能發生的錯誤代碼，此方法。  
  
|值|描述|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|無法開啟檔案或檔案格式無效。|  
|E_PDB_FORMAT|嘗試存取的檔案已經過時的格式。|  
|E_PDB_INVALID_SIG|簽章不符。|  
|E_PDB_INVALID_AGE|年齡不符。|  
|E_INVALIDARG|無效的參數。|  
|E_UNEXPECTED|已備妥資料來源。|  
  
## <a name="remarks"></a>備註  
 .Exe/.dll 檔案的偵錯標頭名稱相關聯的偵錯資料位置。  
  
 這個方法讀取偵錯標頭，然後搜尋並準備偵錯資料。 搜尋的進度可能選擇性地報告並控制透過回呼。 例如， [idialoadcallback:: Notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)時叫用`IDiaDataSource::loadDataForExe`方法找出並處理偵錯目錄。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)和[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)介面可讓用戶端應用程式，以提供替代的方法，從可執行檔讀取資料檔案時檔案無法直接透過標準檔案 I/O 存取。  
  
 若要載入的.pdb 檔不需要驗證，使用[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。  
  
 若要驗證針對特定準則的.pdb 檔，請使用[idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。  
  
 若要直接從記憶體載入.pdb 檔案，請使用[idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。  
  
## <a name="example"></a>範例  
  
```C++  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Idialoadcallback:: Notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [Idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)