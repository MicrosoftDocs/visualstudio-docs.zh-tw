---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150143"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

維護 [IDiaFrameData：： execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 方法調用之間的堆疊內容。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaStackWalkFrame : IUnknown  
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
  
## <a name="requirements"></a>需求  
 標頭： Dia2。h  
  
 程式庫： diaguids .lib  
  
 DLL： msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [ (Debug 介面存取 SDK) 介面 ](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
