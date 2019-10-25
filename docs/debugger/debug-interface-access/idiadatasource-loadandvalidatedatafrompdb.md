---
title: IDiaDataSource：： loadAndValidateDataFromPdb |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97afff946827c37ec2f84457016525377977dc8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744994"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
開啟並確認程式資料庫（.pdb）檔案符合提供的簽章資訊，並準備 .pdb 檔案做為偵錯工具資料來源。

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

在.Pdb 檔案的路徑。

`pcsig70`

在要針對 .pdb 檔案簽章驗證的 GUID 簽章。 只有 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 和更新版本中的 .pdb 檔案具有 GUID 簽章。

`sig`

在要針對 .pdb 檔案簽章驗證的32位簽章。

`age`

在要驗證的存留期值。 年齡不一定會對應到任何已知的時間值，而是用來判斷 .pdb 檔案是否與對應的 .exe 檔案不同步。

## <a name="return-value"></a>傳回值
如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。 下表顯示這個方法的可能傳回值。

|值|描述|
|-----------|-----------------|
|E_PDB_NOT_FOUND|無法開啟檔案，或檔案的格式無效。|
|E_PDB_FORMAT|嘗試存取具有過時格式的檔案。|
|E_PDB_INVALID_SIG|簽章不相符。|
|E_PDB_INVALID_AGE|年齡不相符。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|資料來源已準備就緒。|

## <a name="remarks"></a>備註
.Pdb 檔案同時包含簽章和 age 值。 這些值會在 .exe 或 .dll 檔案中複寫，以符合 .pdb 檔案。 準備資料來源之前，這個方法會驗證指定的 .pdb 檔案的簽章和年齡是否符合所提供的值。

若要載入不具驗證的 .pdb 檔案，請使用[IDiaDataSource：： loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。

若要取得資料載入進程（透過回呼機制）的存取權，請使用[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。

若要直接從記憶體載入 .pdb 檔案，請使用[IDiaDataSource：： loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。

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

## <a name="see-also"></a>請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
