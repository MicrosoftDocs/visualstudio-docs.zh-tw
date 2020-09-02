---
title: IDebugLoadCompleteEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugLoadCompleteEvent2
helpviewer_keywords:
- IDebugLoadCompleteEvent2
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cc3e689f640211d070802432f7944e19e094498
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685985"
---
# <a name="idebugloadcompleteevent2"></a>IDebugLoadCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面是由 debug 引擎傳送， (在載入程式時，但在執行任何程式碼之前，將) 還原為會話 debug manager (SDM) 。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugLoadCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 DE 會執行這個介面，以報告程式是否已成功載入。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 來存取 `IDebugEvent2` 介面。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 「取消」會建立並傳送此事件物件，以報告程式已順利載入。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。  
  
## <a name="remarks"></a>備註  
 此事件是停止事件，而且必須在 `EVENT_STOPPING` 事件屬性上設定旗標。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
