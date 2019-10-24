---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741514"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
提供方法，以使用 .pdb 檔案中的資訊進行堆疊的逐步解說。

## <a name="syntax"></a>語法

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示 `IDiaStackWalker` 的方法。

|方法|描述|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|抓取 x86 平臺的堆疊框架列舉值。|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|抓取特定平臺類型的堆疊框架列舉值。|

## <a name="remarks"></a>備註
這個介面是用來取得已載入模組的堆疊框架清單。 每個方法都會傳遞一個[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)物件（由用戶端應用程式所執行），以提供建立堆疊框架清單所需的資訊。

## <a name="notes-for-callers"></a>呼叫者的注意事項
這個介面是藉由呼叫具有類別識別碼 `CLSID_DiaStackWalker` 的 `CoCreateInstance` 方法，以及 `IID_IDiaStackWalker` 的介面識別碼來取得。 此範例會顯示如何取得此介面。

## <a name="example"></a>範例
這個範例會示範如何取得 `IDiaStackWalker` 介面。

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
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
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
