---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 453be1d77f1d2b1759e3de4433225cf97d026054
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744910"
---
# <a name="idiadatasource"></a>IDiaDataSource
起始對調試符號來源的存取。

## <a name="syntax"></a>語法

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示 `IDiaDataSource` 的方法。

|方法|描述|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|抓取上一個載入錯誤的檔案名。|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|開啟並準備程式資料庫（.pdb）檔案做為 debug 資料來源。|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|開啟並確認程式資料庫（.pdb）檔案符合提供的簽章資訊;準備 .pdb 檔案做為 debug 資料來源。|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|開啟並準備與 .exe/.dll 檔案相關聯的 debug 資料。|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|準備儲存在程式資料庫（.pdb）檔案中的 debug 資料，此檔案會透過記憶體中的資料流程來存取。|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|開啟查詢符號的會話。|

## <a name="remarks"></a>備註
呼叫 `IDiaDataSource` 介面的其中一個 load 方法會開啟符號來源。 成功呼叫[IDiaDataSource：： openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)方法會傳回支援查詢資料來源的[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面。 如果 load 方法傳回與檔案相關的錯誤，則[IDiaDataSource：： get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)方法傳回值會包含與錯誤相關聯的檔案名。

## <a name="notes-for-callers"></a>呼叫者的注意事項
這個介面是藉由呼叫具有類別識別碼 `CLSID_DiaSource` 的 `CoCreateInstance` 函式，以及 `IID_IDiaDataSource` 的介面識別碼來取得。 此範例會顯示如何取得此介面。

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
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
