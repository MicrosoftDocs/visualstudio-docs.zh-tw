---
description: 開啟並準備程式資料庫 ( .pdb) 檔案做為偵錯工具資料來源。
title: IDiaDataSource：： loadDataFromPdb |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0766d951068c237e47f563a8d2ed5b3c84a9d74e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158257"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
開啟並準備程式資料庫 ( .pdb) 檔案做為偵錯工具資料來源。

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
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示此方法可能傳回的值。

|值|描述|
|-----------|-----------------|
|E_PDB_NOT_FOUND|無法開啟檔案，或判定檔案的格式無效。|
|E_PDB_FORMAT|嘗試存取已淘汰格式的檔案。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|已經備妥資料來源。|

## <a name="remarks"></a>備註
這個方法會直接從 .pdb 檔案載入調試資料。

若要根據特定準則驗證 .pdb 檔案，請使用 [IDiaDataSource：： loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 方法。

若要透過) 的回呼機制取得資料載入進程 (的存取權，請使用 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。

若要直接從記憶體載入 .pdb 檔案，請使用 [IDiaDataSource：： loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) 方法。

## <a name="example"></a>範例

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>另請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
