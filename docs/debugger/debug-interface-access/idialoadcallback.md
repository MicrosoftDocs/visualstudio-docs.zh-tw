---
description: 從 DIA 符號尋找程式接收回呼，因此可讓使用者介面報告位置嘗試的進度。
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a283a40ae39c53a4a96f80adb633b92ba68f637
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157466"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
從 DIA 符號尋找程式接收回呼，因此可讓使用者介面報告位置嘗試的進度。

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 此介面會公開下列方法：

|方法|描述|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|當在 .exe 檔中找到 debug 目錄時呼叫。|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|在開啟候選的 dbg 檔案時呼叫。|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|在開啟候選 .pdb 檔案時呼叫。|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|決定是否可以使用登錄查詢來尋找符號搜尋路徑。|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|決定是否允許符號伺服器存取符號，以解析符號。|

## <a name="remarks"></a>備註
 用戶端應用程式會執行這個介面，並在 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法的呼叫中提供它的參考。

 如需可加諸于載入進程的其他限制，請參閱 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) 介面。

## <a name="requirements"></a>規格需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
