---
title: IDiaDataSource：： loadDataFromPdb |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744930"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
開啟並準備程式資料庫（.pdb）檔案做為 debug 資料來源。

## <a name="syntax"></a>語法

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>參數
pdbPath

在.Pdb 檔案的路徑。

## <a name="return-value"></a>傳回值
如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。 下表顯示這個方法的可能傳回值。

|值|描述|
|-----------|-----------------|
|E_PDB_NOT_FOUND|無法開啟檔案，或判定檔案的格式無效。|
|E_PDB_FORMAT|嘗試存取具有過時格式的檔案。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|資料來源已準備就緒。|

## <a name="remarks"></a>備註
這個方法會直接從 .pdb 檔案載入調試資料。

若要根據特定準則來驗證 .pdb 檔案，請使用[IDiaDataSource：： loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。

若要取得資料載入進程（透過回呼機制）的存取權，請使用[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。

若要直接從記憶體載入 .pdb 檔案，請使用[IDiaDataSource：： loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。

## <a name="example"></a>範例

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
