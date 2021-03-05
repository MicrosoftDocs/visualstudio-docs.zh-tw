---
description: 起始對偵測符號來源的存取。
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4932b3c787e1d17b5b32ea6a32bdd604692bda4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158243"
---
# <a name="idiadatasource"></a>IDiaDataSource
起始對偵測符號來源的存取。

## <a name="syntax"></a>Syntax

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaDataSource` 。

|方法|描述|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|抓取最後載入錯誤的檔案名。|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|開啟並準備程式資料庫 ( .pdb) 檔案做為偵錯工具資料來源。|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|開啟並確認程式資料庫 ( .pdb) 檔案符合提供的簽章資訊;將 .pdb 檔案準備為 debug 資料來源。|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|開啟並準備與 .exe/.dll 檔案相關聯的調試資料。|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|準備程式資料庫中儲存的 debug 資料 ( .pdb) 透過記憶體中資料流程存取的檔案。|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|開啟用於查詢符號的會話。|

## <a name="remarks"></a>備註
對介面的其中一個 load 方法進行呼叫 `IDiaDataSource` 會開啟符號來源。 成功呼叫 [IDiaDataSource：： openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 方法會傳回支援查詢資料來源的 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 介面。 如果 load 方法傳回檔案相關的錯誤，則 [IDiaDataSource：： get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) 方法傳回值會包含與錯誤相關聯的檔案名。

## <a name="notes-for-callers"></a>呼叫者注意事項
藉由呼叫 `CoCreateInstance` 具有類別識別碼 `CLSID_DiaSource` 和之介面識別碼的函式，即可取得這個介面 `IID_IDiaDataSource` 。 此範例顯示如何取得此介面。

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

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
