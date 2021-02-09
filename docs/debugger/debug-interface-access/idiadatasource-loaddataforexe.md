---
title: IDiaDataSource：： loadDataForExe |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cd56e200ffe382cf8803598d9a1006403aeb393
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865255"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
開啟並準備與 .exe/.dll 檔案相關聯的調試資料。

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

在.Exe 或 .dll 檔案的路徑。

searchPath

在用來搜尋 debug 資料的替代路徑。

pCallback

在 `IUnknown` 支援 debug 回檔介面之物件的介面，例如 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)、 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)、 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)和/或 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) 介面。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示這個方法的一些可能的錯誤碼。

|值|描述|
|-----------|-----------------|
|E_PDB_NOT_FOUND|無法開啟檔案，或檔案的格式無效。|
|E_PDB_FORMAT|嘗試存取已淘汰格式的檔案。|
|E_PDB_INVALID_SIG|簽章不相符。|
|E_PDB_INVALID_AGE|Age 不符。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|已經備妥資料來源。|

## <a name="remarks"></a>備註
.Exe/.DLL 檔案名的 debug 標頭會將相關聯的 debug 資料位置命名為。

這個方法會讀取 debug 標頭，然後搜尋並準備偵錯工具資料。 搜尋的進度可選擇性地透過回呼報告及控制。 例如， [IDiaLoadCallback：： NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) 會在 `IDiaDataSource::loadDataForExe` 方法尋找並處理 debug 目錄時叫用。

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)和[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)介面可讓用戶端應用程式在無法透過標準檔案 i/o 直接存取檔案時，提供從可執行檔讀取資料的替代方法。

若要載入不含驗證的 .pdb 檔，請使用 [IDiaDataSource：： loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 方法。

若要根據特定準則驗證 .pdb 檔案，請使用 [IDiaDataSource：： loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 方法。

若要直接從記憶體載入 .pdb 檔案，請使用 [IDiaDataSource：： loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) 方法。

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
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
