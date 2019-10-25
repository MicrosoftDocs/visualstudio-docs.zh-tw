---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b2657127726e387e81a5b28c639abbaa5399019
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741433"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
維護[IDiaFrameData：： execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法調用之間的堆疊內容。

## <a name="syntax"></a>語法

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示 `IDiaStackWalkFrame` 的方法。

|方法|描述|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|抓取暫存器的值。|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|設定註冊的值。|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|從影像讀取記憶體。|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|在指定的堆疊框架中搜尋最接近的函式傳回位址。|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|在指定的堆疊框架中，搜尋位於或接近指定位址的傳回位址。|

## <a name="remarks"></a>備註
 此介面會在程式執行期間用來讀取和寫入暫存器，以及存取記憶體和尋找傳回位址。

## <a name="notes-for-callers"></a>呼叫者的注意事項
 用戶端應用程式會執行此介面，並將介面的實例傳遞至[IDiaFrameData：： execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。 再次使用此介面的相同實例，以在每次叫用 `execute` 方法時維護暫存器的狀態。 @No__t_0 方法也會使用這個介面來判斷傳回位址。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)