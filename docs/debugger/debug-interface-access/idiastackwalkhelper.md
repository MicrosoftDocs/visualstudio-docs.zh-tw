---
title: "IDiaStackWalkHelper |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6cbd88bbe3e8a752721047ee80d847e72cf115b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
可加速，查核堆疊使用的程式偵錯資料庫 (.pdb) 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>依照 VTable 順序的方法  
 下表顯示的方法`IDiaStackWalkHelper`:  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|擷取暫存器的值。|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|設定暫存器的值。|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|讀取的可執行檔映像，在記憶體中的資料區塊。|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|搜尋指定的堆疊框架的最接近的函式傳回的位址。|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|搜尋指定的堆疊框架，位於或接近指定之堆疊位址的回覆地址的。|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|擷取堆疊框架，其中包含指定的虛擬位址。|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|擷取包含指定的虛擬位址的符號。 **注意：**符號的型別必須`SymTagFunctionType`(介於[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別)。|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|傳回與指定的虛擬位址相關聯的 PDATA 資料區塊。|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|擷取可執行檔開始虛擬位址的虛擬位址某處的可執行檔的記憶體空間中。|  
  
## <a name="remarks"></a>備註  
 DIA 程式碼，以取得資訊的可執行檔，來建構堆疊框架的清單，在程式執行期間會呼叫這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 用戶端應用程式會實作這個介面以支援在程式執行期間查核堆疊。 此介面的執行個體傳遞至[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)或[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)