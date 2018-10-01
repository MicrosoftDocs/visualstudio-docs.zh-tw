---
title: IDiaStackWalkFrame |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c525d2c19f3bc4ab7ea540ac129931583064db01
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485316"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaStackWalkFrame](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkframe)。  
  
會維護引動過程之間的堆疊內容[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaStackWalkFrame`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|擷取暫存器的值。|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|設定暫存器值。|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|讀取影像中的記憶體。|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|搜尋指定的堆疊框架之最接近的函式傳回的位址。|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|搜尋指定的堆疊框架的地址，位於或接近指定的位址。|  
  
## <a name="remarks"></a>備註  
 此介面用在程式執行期間，讀取和寫入暫存器，以及存取的記憶體和尋找傳回的位址。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 用戶端應用程式會實作這個介面，並將傳遞至介面的執行個體[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。 每次叫用期間，維持狀態的暫存器一次又一次使用相同的執行個體，這個介面的`execute`方法。 `execute`方法也使用此介面來判斷傳回的位址。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)



