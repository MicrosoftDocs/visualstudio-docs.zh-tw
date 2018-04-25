---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e298edac96b311e8e25e41698aaa3db539ec154
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
開啟和驗證的程式資料庫 (.pdb) 檔案符合簽章提供的資訊，並準備做為偵錯資料來源的.pdb 檔案。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdbPath`  
 [in].Pdb 檔案的路徑。  
  
 `pcsig70`  
 [in]若要驗證的.pdb 檔案簽章的 GUID 簽章。 只有.pdb 檔案中[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]和更新版本有 GUID 簽章。  
  
 `sig`  
 [in]32 位元簽章來進行驗證的.pdb 檔案簽章。  
  
 `age`  
 [in]若要驗證的年齡值。 存在時間不一定會對應到任何已知的時間值，它用來判斷是否與對應的.exe 檔案同步處理的.pdb 檔案。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|無法開啟檔案或檔案格式無效。|  
|E_PDB_FORMAT|嘗試存取的檔案已經過時的格式。|  
|E_PDB_INVALID_SIG|簽章不符。|  
|E_PDB_INVALID_AGE|年齡不符。|  
|E_INVALIDARG|無效的參數。|  
|E_UNEXPECTED|已備妥資料來源。|  
  
## <a name="remarks"></a>備註  
 .Pdb 檔案中包含簽章和年齡的值。 這些值中的.exe 或.dll 檔案符合.pdb 檔複寫。 準備之前的資料來源，這個方法會驗證具名的.pdb 檔案的簽章和年齡符合所提供的值。  
  
 若要載入的.pdb 檔不需要驗證，使用[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。  
  
 若要存取的資料載入程序 （透過回呼機制），請使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
 若要直接從記憶體載入.pdb 檔案，請使用[idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。  
  
## <a name="example"></a>範例  
  
```C++  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)