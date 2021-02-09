---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98887e684d9bf2cbe282b7d9c4670fd18a355bd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864534"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
讓用戶端應用程式提供相對虛擬位址所指定的可執行檔位元組。

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDiaReadExeAtRVACallback` 。

|方法|描述|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|從可執行檔 (RVA) 中，讀取指定的相對虛擬位址開始的指定位元組數目。|

## <a name="remarks"></a>備註
 用戶端應用程式會執行這個介面，以便使用相對虛擬位址，將可執行檔的位元組提供給可執行檔。 若要使用絕對檔案位移，請執行 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個方法是由用戶端應用程式所執行，並傳遞至 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法，作為讀取檔案的替代方法。

## <a name="requirements"></a>規格需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)