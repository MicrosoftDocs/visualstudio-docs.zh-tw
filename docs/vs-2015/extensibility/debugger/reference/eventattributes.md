---
title: EVENTATTRIBUTES |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3026845be9aa6623d6c5cd42406385e8c5c2a11e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149367"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定事件屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>成員  
 EVENT_ASYNCHRONOUS  
 表示事件是非同步，而且不需要回復事件。  
  
 EVENT_SYNCHRONOUS  
 表示事件是同步的;以 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)的方式回復。  
  
 EVENT_STOPPING  
 表示這是停止事件。 必須與 `EVENT_ASYNCHRONOUS` 或結合 `EVENT_SYNCHRONOUS` 。  
  
 EVENT_ASYNC_STOP  
 表示非同步停止事件。 目前沒有這類事件。 此旗標只是預留位置。  
  
 EVENT_SYNC_STOP  
 表示同步停止事件 (和) 的組合 `EVENT_SYNCHRONOUS` `EVENT_STOPPING` 。 此值是由偵錯工具引擎在傳送停止事件時 (DE) 使用。 回復是藉由呼叫 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)、 [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)或 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)來進行。  
  
 EVENT_IMMEDIATE  
 表示立即和同步傳送至 IDE 的事件。 此旗標會與其他旗標（例如 `EVENT_ASYNCHRONOUS` 、 `EVENT_SYNCHRONOUS` 或）結合， `EVENT_SYNC_STOP` 以表示事件的類型，以及當已知任何) 時，回復機制 (的事實。  
  
 EVENT_EXPRESSION_EVALUATION  
 事件是運算式評估的結果。  
  
## <a name="remarks"></a>備註  
 這些值會以 `dwAttrib` [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 方法的參數傳遞。  
  
 這些值可能會與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
