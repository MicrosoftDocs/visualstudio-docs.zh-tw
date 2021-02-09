---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84661f5cd51da17cf20577490b2fe458e71ef71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863736"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
使用「程式偵錯工具」資料庫 ( .pdb) 檔來加速堆疊。

## <a name="syntax"></a>Syntax

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDiaStackWalkHelper` 如下：

|方法|描述|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|捕獲暫存器的值。|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|設定註冊的值。|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|從記憶體中的可執行檔映射讀取資料區塊。|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|搜尋指定的堆疊框架是否有最接近的函數傳回位址。|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|在指定的堆疊框架中搜尋指定堆疊位址的或附近的傳回位址。|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|抓取包含指定虛擬位址的堆疊框架。|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|抓取包含指定之虛擬位址的符號。 **注意：**  符號的類型必須 `SymTagFunctionType` 是 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 列舉) 的值 (。|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|傳回與指定的虛擬位址相關聯的 .PDATA 資料區塊。|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|取得可執行檔的起始虛擬位址，指定可執行檔的記憶體空間中某處的虛擬位址。|

## <a name="remarks"></a>備註
 DIA 程式碼會呼叫這個介面，以取得可執行檔的相關資訊，以便在程式執行期間，建立堆疊框架的清單。

## <a name="notes-for-callers"></a>呼叫者注意事項
 用戶端應用程式會在程式執行期間，將此介面實作為支援堆疊。 這個介面的實例會傳遞至 [IDiaStackWalker：： getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) 或 [IDiaStackWalker：： getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) 方法。

## <a name="requirements"></a>規格需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)