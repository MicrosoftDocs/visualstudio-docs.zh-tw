---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05db065b047629e1eaac49e5f6aeeb05eed4307e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863820"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
維護 [IDiaFrameData：： execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 方法調用之間的堆疊內容。

## <a name="syntax"></a>Syntax

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDiaStackWalkFrame` 。

|方法|描述|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|捕獲暫存器的值。|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|設定註冊的值。|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|從映射讀取記憶體。|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|搜尋指定的堆疊框架是否有最接近的函數傳回位址。|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|在指定的堆疊框架中搜尋指定位址或附近的傳回位址。|

## <a name="remarks"></a>備註
 此介面會在程式執行期間用來讀取和寫入暫存器，以及存取記憶體和尋找傳回位址。

## <a name="notes-for-callers"></a>呼叫者注意事項
 用戶端應用程式會執行這個介面，並將介面的實例傳遞至 [IDiaFrameData：： execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 方法。 這個介面的相同實例會再次使用，並在每次叫用方法期間維持暫存器的狀態 `execute` 。 `execute`方法也會使用此介面來判斷傳回位址。

## <a name="requirements"></a>規格需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)