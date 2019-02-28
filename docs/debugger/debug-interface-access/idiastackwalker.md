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
ms.openlocfilehash: 5ad74f92765ee449eab1e3089511a063e70d96a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617063"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
提供方法，以執行堆疊查核行程使用.pdb 檔案中的資訊。

## <a name="syntax"></a>語法

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法`IDiaStackWalker`。

|方法|說明|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|擷取堆疊框架的列舉值適用於 x86 平台。|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|擷取特定平台類型的堆疊框架的列舉值。|

## <a name="remarks"></a>備註
此介面用來取得載入模組的堆疊框架的清單。 每個方法會傳遞[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) （用戶端應用程式所實作） 的物件可提供所需的資訊建立堆疊框架的清單。

## <a name="notes-for-callers"></a>呼叫端資訊
這個介面由呼叫`CoCreateInstance`方法的類別識別項`CLSID_DiaStackWalker`而介面 ID 的`IID_IDiaStackWalker`。 此範例會示範如何取得這個介面。

## <a name="example"></a>範例
此範例示範如何取得`IDiaStackWalker`介面。

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
標頭： Dia2.h

程式庫： diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
