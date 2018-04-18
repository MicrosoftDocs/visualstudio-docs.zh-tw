---
title: IDiaStackWalkFrame |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e532323923aaa3c50e00fc685fb39eaf8bfed80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
會維護的引動過程之間的堆疊內容[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaStackWalkFrame`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|擷取暫存器的值。|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|設定暫存器的值。|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|從映像讀取記憶體。|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|搜尋指定的堆疊框架的最接近的函式傳回的位址。|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|搜尋指定的堆疊框架的回覆地址或接近指定的位址。|  
  
## <a name="remarks"></a>備註  
 在程式執行期間會使用這個介面，讀取和寫入暫存器，以及存取的記憶體和尋找地址。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 用戶端應用程式會實作這個介面，並將傳遞至介面的執行個體[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。 相同的執行個體，這個介面一再重複用來在每次叫用期間維持暫存器的狀態`execute`方法。 `execute`方法也使用此介面來判斷傳回的位址。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)