---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40c2b58778b2a1073b31acc7007388d8e8fe222c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741310"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
有助於使用程式 debug 資料庫（.pdb）檔案來進行堆疊的逐步解說。

## <a name="syntax"></a>語法

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示 `IDiaStackWalkHelper` 的方法：

|方法|描述|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|抓取暫存器的值。|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|設定註冊的值。|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|從記憶體中可執行檔的影像讀取資料區塊。|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|在指定的堆疊框架中搜尋最接近的函式傳回位址。|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|在指定的堆疊框架中，搜尋指定之堆疊位址所在或附近的傳回位址。|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|抓取包含指定虛擬位址的堆疊框架。|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|抓取包含指定之虛擬位址的符號。 **注意：** 符號的類型必須 `SymTagFunctionType` （ [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉中的值）。|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|傳回與指定之虛擬位址相關聯的 PDATA 資料區塊。|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|在可執行檔的記憶體空間中某個位置取得虛擬位址，以抓取可執行檔的起始虛擬位址。|

## <a name="remarks"></a>備註
 DIA 程式碼會呼叫這個介面，以取得可執行檔的相關資訊，以在程式執行期間建立堆疊框架清單。

## <a name="notes-for-callers"></a>呼叫者的注意事項
 用戶端應用程式會執行此介面，以支援在程式執行期間流覽堆疊。 這個介面的實例會傳遞至[IDiaStackWalker：： getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)或[IDiaStackWalker：： getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)方法。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)