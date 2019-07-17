---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198624"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

開啟和驗證的程式資料庫 (.pdb) 檔案符合簽章提供的資訊，並準備做為偵錯資料來源的.pdb 檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdbPath`  
 [in].pdb 檔案的路徑。  
  
 `pcsig70`  
 [in]若要驗證的.pdb 檔案簽章的 GUID 簽章。 只有.pdb 檔案中[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]和更新版本中有 GUID 簽章。  
  
 `sig`  
 [in]若要驗證的.pdb 檔案簽章 32 位元簽章。  
  
 `age`  
 [in]若要確認的存留期值。 存留期不一定會對應至任何已知的時間值，它用來判斷是否與對應的.exe 檔案不同步的.pdb 檔案。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。  
  
|值|說明|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|無法開啟檔案，或檔案格式無效。|  
|E_PDB_FORMAT|嘗試存取已過時的格式的檔案。|  
|E_PDB_INVALID_SIG|簽章不符。|  
|E_PDB_INVALID_AGE|年齡不符。|  
|E_INVALIDARG|無效的參數。|  
|E_UNEXPECTED|資料來源已準備好了。|  
  
## <a name="remarks"></a>備註  
 .Pdb 檔案中包含簽章和存留期值。 這些值會複寫.exe 或.dll 檔案與相符的.pdb 檔案中。 準備之前的資料來源，這個方法會驗證已命名的.pdb 檔案的簽章和年齡，符合所提供的值。  
  
 若要載入的.pdb 檔不需要驗證，使用[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。  
  
 若要存取的資料載入程序 （透過回呼的機制），請使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
 若要直接從記憶體中載入的.pdb 檔案，請使用[idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。  
  
## <a name="example"></a>範例  
  
```cpp#  
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
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
